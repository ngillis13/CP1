<template>
  <div>
    <div class="rates" v-for="rating in ratings" v-bind:key="rating._id">
      <div class="ratingInfo">
        <p class="Name">{{rating.title}}</p>
        <p class="Rate">{{rating.rating}}</p>
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import axios from 'axios';

export default {
  name: "MovieRate",
  data() {
    return {
      title: '',
      rating: '',
      comments: '',
      error: '',
      ratings: this.getRatings(),
    }
  },
  
  methods: {
    close() {
      this.$emit('close');
    },
    async upload() {
      try {
        const formData = new FormData();
        formData.append('photo', this.file, this.file.name);
        formData.append('title', this.title);
        formData.append('description', this.description);
        await axios.post("/api/photos", formData);
        this.file = null;
        this.url = "";
        this.title = "";
        this.description = "";
        this.$emit('uploadFinished');
      } catch (error) {
        this.error = "Error: " + error.response.data.message;
      }
    },
    async getRatings() {
        try {
          let response = await axios.get("/api/rating/all");
          this.ratings = response.data
        } catch(error){
          console.log(error);
        }

    }
  }
  
}


</script>

<style>

.form-data {
    margin: 10px;
}

fieldset {
    margin: 20px;
}

</style>