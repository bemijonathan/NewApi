<template>
  <div class="about">
    <h1 class="title">This is an {{this.$route.params.category}} HeadLines for Today</h1>
    <b-loading :is-full-page="false" :active.sync="isLoading" :can-cancel="false"></b-loading>
    <div class="container">
      <Card :props="news" />
    </div>
  </div>
</template>
<script>
import axios from "axios";
import Card from "@/components/card";
export default {
  data() {
    return {
      news: [],
      isLoading: false
    };
  },
  components: {
    Card
  },
  methods: {
    async getNews() {
      try {
        this.isLoading = true;
        const job = await axios.get(
          "https://newsapi.org/v2/everything?q=" +
            this.$route.params.category +
            "&apiKey=822c5e287d7e41139c654a0e462ba9e5"
        );
        console.log(job);
        this.news = job.data.articles.splice(10);
      } catch (error) {
        // this.isLoading = false;
        console.log(error);
      }

      this.isLoading = false;
    }
  },
  async mounted() {
    this.getNews();
  },
  watch: {
    $route() {
      this.getNews();
    }
  }
};
</script>

<style>
.about {
  margin-top: 35px;
}
</style>


https://newsapi.org/v2/everything?q=bitcoin&apiKey=822c5e287d7e41139c654a0e462ba9e5