<template>
  <div class="col-3">
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
</template>

<script>
export default {
    name: 'discoCard',

    props:{
        disco: Object,
    }
}
</script>

<style lang="scss" scoped>
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

  .card_title{
    color: $text_light;
  }

  .card-text, .small_text{
    color: $text_dark;
  }

</style>