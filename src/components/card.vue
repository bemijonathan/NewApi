<template>
  <section class="columns cardcomponent is-desktop">
    <!-- {{props}} -->
    <section class="column is-half" v-for="(news ,i) in props" :key="i">
      <div class="card" >
        <div class="card-content columns">
          <div class="column">
            <div class="card-image">
              <figure class="image is-4by3">
                <img
                  :src="news.urlToImage? news.urlToImage: 'https://bulma.io/images/placeholders/1280x960.png' "
                  alt="Placeholder image"
                />
              </figure>
            </div>
            
          </div>

          <div class="column">
            <p class="text-is-left">{{news.title}}</p>
            <p details> source : <a>{{news.source.name}}</a>
            <br />
            Date : <time datetime="2016-1-1">{{ new Date(news.publishedAt).toDateString() }}</time>
            </p>
            
            <div class="media-content">
              <p class=" is-4">Author: {{news.author}}</p>
              <a :href="news.url"> Read More </a>
            </div>
          </div>
        </div>
      </div>
    </section>
  </section>
</template>

<script>
export default {
  props:['props']
};
</script>

<style>
[details]{
  text-align:left
}
.cardcomponent{
    padding: 35px 0;
}
.cardcomponent.columns{
    flex-wrap: wrap;
    align-items: center;
    justify-content: center;   
}
.cardcomponent .card{
    margin-top: 20px !important;
}
.text-is-left{
    /* text-align: left !important; */
    text-align: left !important;
    font-size: 21px;
    font-weight: 800;
}
time{
    text-align: left !important;
}
@media screen and (max-width: 500px){
    .card{
        margin:10px;
        overflow: hidden;    
    }
    .text-is-left{
    text-align: left !important;
    font-size: 17px;
  }
}
</style>