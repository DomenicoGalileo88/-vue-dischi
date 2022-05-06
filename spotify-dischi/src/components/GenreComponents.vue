<template>
   <form class="d-flex justify-content-center" @change="$emit('formGenre')">
      <select
        name="genre"
        :value="changeGenre"
        @input="$emit('input', $event.target.value)"
        @change="$emit('formGenre', changeGenre)"
      >
      <option value="jazz">Jazz</option>
      <option value="rock">Rock</option>
      <option value="Metal">Metal</option>
      <option value="pop">Pop</option>
      </select>
      <button
        class="btn btn-outline-success d-flex align-items-center ms-2"
        :disabled="changeGenre < 1"
      >
        Search
      </button>
    </form>
</template>

<script>
export default {
    name: 'GenreComponents',
    props:{
        changeGenre: Object,
    }
}
</script>

<style lang="scss" scoped>

</style>