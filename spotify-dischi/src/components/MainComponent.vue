<template>
  <main>
    <div class="container">
      <div class="row" v-if="loading">
        <div class="col-3" v-for="(disco, index) in dischi" :key="index">
            <div class="card">
              <img :src="disco.poster" class="card-img-top" :lt="disco.author" />
              <div class="card-body">
                <h5 class="card-title">{{disco.title}}</h5>
                <p class="card-text">
                  {{disco.author}}
                </p>
                <small>{{disco.year}}</small>
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
  height: 500px;
  background-color: rgb(0, 76, 119);

  .col-3{
    width: 20%;
  }
  img {
    max-width: 100%;
    width: 200px;
    object-fit: cover;
    aspect-ratio: 1/1;
  }
}
</style>