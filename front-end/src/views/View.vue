<template>
  <div class="home">
    <p v-if="user" style="text-align:right; padding: 20px;"><a @click="logout"> Log out</a></p>
    <Selection v-if="user"/>
    <ViewRatings v-if="user"/>
    <login v-else/>
  </div>
</template>

<script>
import axios from 'axios';
import login from '@/components/login.vue';
import Selection from '@/components/Selection.vue';
import ViewRatings from '@/components/ViewRatings.vue';

export default {
  name: 'View',
  components: {
    login,
    Selection,
    ViewRatings 
  },
  async created() {
    try {
      let response = await axios.get('/api/users');
      this.$root.$data.user = response.data.user;
    } catch (error) {
      this.$root.$data.user = null;
    }
  },
  computed: {
    user() {
      return this.$root.$data.user;
    }
  },
  methods: {
    async logout() {
      try {
        await axios.delete("/api/users");
        this.$root.$data.user = null;
      } catch (error) {
        this.$root.$data.user = null;
      }
    },
  }
}
</script>
