<template>
  <div class="container home">
    <h1 class="title">Trending</h1>

    <section>
      <b-carousel :icon-prev="'arrow-left'" :icon-next="'arrow-right'" :icon-size="''">
        <b-carousel-item v-for="(carousel, i) in carousels" :key="i">
          <section :class="`hero is-medium is-${carousel.color}`">
            <div class="hero-body has-text-centered">
              <h1 class="title">{{carousel.title}}</h1>
            </div>
          </section>
        </b-carousel-item>
      </b-carousel>
    </section>
    <b-loading :is-full-page="false" :active.sync="isLoading" :can-cancel="false"></b-loading>
    <section>
      <Card :props="news" />
    </section>
  </div>
</template>

<script>
import axios from "axios";
import Card from "@/components/card";
export default {
  name: "Home",
  data() {
    return {
      carousels: [
        { title: "Tech", color: "info" },
        { title: "Business", color: "success" },
        { title: "Health", color: "warning" },
        { title: "Politics", color: "danger" }
      ],
      news: [],
      isLoading: false
    };
  },
  components: {
    Card
  },
  async mounted() {
    this.isLoading = true;
    try {
      const job = await axios.get(
        "https://newsapi.org/v2/top-headlines?" +
          "country=us&" +
          "apiKey=822c5e287d7e41139c654a0e462ba9e5"
      );
      console.log(job);
      this.news = job.data.articles.splice(10);
    } catch (error) {
      console.log(error);
    }

    this.isLoading = false;
  }
};
</script>


<style>
.home .title {
  margin-top: 25px;
}
</style>


822c5e287d7e41139c654a0e462ba9e5

http://newsapi.org/v2/top-headlines