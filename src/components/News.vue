<template>
        <div class="news-list">
          <b-list-group>
            <item v-for="(news,index) of newsList" :key="index" v-bind:news="news"></item>
            </b-list-group>
        </div>
</template>

<script>
import axios from "axios";
import item from "./Item";

import virtualList from "vue-virtual-scroll-list";

export default {
  data() {
    return {
      newsList: [],
      errors: []
    };
  },
  components: { item, "virtual-list": virtualList },

  // Fetches posts when the component is created.
  created() {
    axios
      .get(`/api/v1.0/news`)
      .then(response => {
        // JSON responses are automatically parsed.
        this.newsList = response.data;
      })
      .catch(e => {
        this.errors.push(e);
      });

    // async / await version (created() becomes async created())
    //
    // try {
    //   const response = await axios.get(`http://jsonplaceholder.typicode.com/posts`)
    //   this.posts = response.data
    // } catch (e) {
    //   this.errors.push(e)
    // }
  }
};
</script>
<style>
.news-list {
  height: 100%;
  width: 65%;
  margin: auto;
}
.list-group-item {
  background-color: transparent !important;
  border: none !important;
}
</style>
