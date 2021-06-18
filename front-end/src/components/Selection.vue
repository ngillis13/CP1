<template>
<div class="hero">
  <div class="buttons">
    <router-link to="/rate"><button class="pure-button pure-button-primary">Rate a Movie</button></router-link>
    <router-link to="/view"><button class="pure-button pure-button-primary">View Ratings</button></router-link>
  </div>
</div>
</template>

<script>
//import axios from 'axios';
//import rate from '@/components/rate.vue';
//import view from '@/components/view.vue';
export default {
  name: "Selection",
  props: {
    isRate: Boolean,
    isView: Boolean,
  },
  data() {
    return {
      
    }
  },
  created() {
    //isRate = false;
    //isView = false;
  },
  //components: {
  //    rate,    
  //},
  methods: {
    async rate() {
        try {
          //isView = false;
          //isRate = true;
        } catch (error) {
          console.log(error);
        }
      },
  }
}


</script>



<style>

.buttons {
  display: flex;
  justify-content: center;
}

</style>
