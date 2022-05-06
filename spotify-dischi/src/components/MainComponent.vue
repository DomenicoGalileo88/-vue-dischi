<template>
  <main>
    <div class="container">
      <SelectDiscGenere v-model="genere" @selezionaGenere="selectGenere"></SelectDiscGenere>
    
      <div class="row" v-if="loading">
        <discoCard
          :disco="disco"
          v-for="(disco, index) in filterGenere"
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
import axios from "axios";
import SelectDiscGenere from '@/components/SelectDiscGenere.vue';
import state from '@/state.js';

export default {
  name: "MainComponent",

  components: {
    discoCard,
    SelectDiscGenere,
  },
  data() {
    return {
      API_url: "https://flynn.boolean.careers/exercises/api/array/music",
      loading: false,
      dischi: null,
      error: "Sorry there are problems, please try again later....",
      genere: '',
    };
  },

  methods: {
    selectGenere() {
      console.log("Hai selezionato un genere");
      console.log(this.genere);
      state.genere = this.genere;
      console.log(state);
    },
  },

  computed: {
    filterGenere(){
      if (state.genere) {
        console.log(state.genere);
        return this.dischi.filter(disco => {
       return disco.genre.toLowerCase().includes(state.genere.toLowerCase())
      })
      } else {
        return this.dischi
      }
    }
  },

  mounted() {
    axios.get(this.API_url).then((response) => {
      /* console.log(this); */
      //console.log(response);
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