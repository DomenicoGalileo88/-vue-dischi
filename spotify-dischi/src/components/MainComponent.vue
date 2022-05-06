<template>
  <main>
    <GenreComponents v-model="selectedGenre" @formSubmit="selectedGenre" />
    <div class="container">
      <div class="row" v-if="loading">
        <discoCard
          :disco="disco"
          v-for="(disco, index) in dischi"
          :key="index"
        />
      </div>
      <!-- /.row -->

      <div class="row" v-else>
        <h1 class="text-white">{{ error }}</h1>
      </div>
    </div>
    <!-- /.container -->
  </main>
</template>

<script>
import discoCard from "@/components/DiscoCardComponent.vue";
import GenreComponents from "@/components/GenreComponents.vue";
import axios from "axios";

export default {
  name: "MainComponent",

  components: {
    discoCard,
    GenreComponents,
  },
  data() {
    return {
      API_url: "https://flynn.boolean.careers/exercises/api/array/music",
      loading: false,
      dischi: null,
      error: "Sorry there are problems, please try again later....",
      changeGenre: null,
    };
  },

  methods: {
    selectedGenre() {
      console.log("Hai selezionato un genere");
    },
  },

  mounted() {
    axios.get(this.API_url).then((response) => {
      /* console.log(this); */
      console.log(response);
      this.dischi = response.data.response;
      this.loading = true;
    });
  },
};
</script>

<style lang="scss" scoped>
main {
  background-color: $main_bg;
  .row {
    padding: 3rem 0;
  }
}
</style>