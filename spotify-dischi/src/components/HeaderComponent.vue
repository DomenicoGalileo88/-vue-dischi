<template>
  <header>
      <div class="logo">
      <img width="40" src="@/assets/img/logo-small.svg" alt="Spotify logo">
  </div>
  </header>
</template>

<script>
export default {
    name: 'HeaderComponent',
};
</script>

<style lang="scss" scoped>
    header{
        background-color: rgb(12, 118, 153);
        padding: 0.7rem;
        img{
    width: 40px;
}
    }
</style>