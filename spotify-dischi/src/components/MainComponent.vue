<template>
  <main>
    <div class="container">
      <div class="row" v-if="loading">
        <div class="col-3" v-for="(disco, index) in dischi" :key="index">
            <div class="card">
              <img :src="disco.poster" class="card-img-top" :lt="disco.author" />
              <div class="card-body">
                <h6 class="card_title text-uppercase">{{disco.title}}</h6>
                <p class="card-text m-0">
                  {{disco.author}}
                </p>
                <small class="small_text">{{disco.year}}</small>
              </div>
            </div>
        </div>
      </div>
    </div>
  </main>
</template>

<script>
import axios from "axios";

export default {
  name: "MainComponent",
  data() {
    return {
      API_url: "https://flynn.boolean.careers/exercises/api/array/music",
      loading: false,
      dischi: null,
      /* error: null, */
    };
  },

  mounted() {
    axios.get(this.API_url).then((response) => {
      /* console.log(this); */
      console.log(response);
      this.dischi = response.data.response;
      this.loading = true;
    });
    /* .catch((error) => {
        console.log(error);
        this.error = 'Sorry there are problems, please try again later.'
      }) */
  },
};
</script>

<style lang="scss" scoped>
main {
  background-color: $main_bg;

  .col-3{
    width: 18%;
    margin: 0.5rem;
  }
  img {
    max-width: 90%;
    object-fit: cover;
    aspect-ratio: 1/1;
    padding: 1rem;
  }

  .card{
    display: flex;
    align-items: center;
    height: 100%;
    background-color: $header_bg;
    border: none;
    text-align: center;
  }

  .row{
    padding: 3rem 0;
  }

  .card_title{
    color: $text_light;
  }

  .card-text, .small_text{
    color: $text_dark;
  }
}
</style>