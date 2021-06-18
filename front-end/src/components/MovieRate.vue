<template>
<div class = "form-data">
    <form class="form" @submit.prevent="upload">
        <p> Tell us about your movie </p>
        <fieldset>
            <input v-model="title" placeholder="Enter name of movie">
        </fieldset>
        <fieldset>
            <input v-model="rating" placeholder="Enter rating for movie (1-10)">
        </fieldset>
        <fieldset>
            <textarea v-model="comments" placeholder="Comments"></textarea>
        </fieldset>
        <fieldset class="buttons">
            <button type="button" @click="close" class="pure-button">Close</button>
            <button type="submit" class="pure-button pure-button-primary right">Upload</button>
        </fieldset>
    </form>

</div>
</template>

<script>
import axios from 'axios';

export default {
  name: "MovieRate",
  props: {
    show: Boolean,
  },
  data() {
    return {
      title: '',
      rating: '',
      comments: '',
      error: '',
    }
  },
  methods: {
    close() {
      this.$emit('close');
    },
    async upload() {
      try {
        console.log(this.title);
        var rateData = new FormData();
        rateData.append("title", this.title);
        console.log(rateData);
        await axios.post("/api/rating", rateData);
        this.rating = "";
        this.title = "";
        this.comments = "";
        this.$emit('uploadFinished');
      } catch (error) {
        this.error = "Error: " + error.response.data.message;
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