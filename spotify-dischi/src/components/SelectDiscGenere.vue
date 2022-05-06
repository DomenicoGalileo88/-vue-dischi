<template>
  <form class="pt-4" @change="$emit('selezionaGenere')">
    <label class="text-white me-2">Filtra per genere</label>
    <select
      name="genre"
      :value="genere"
      @input="$emit('input', $event.target.value)"
    >
      <option value="">All</option>
      <option value="jazz">Jazz</option>
      <option value="rock">Rock</option>
      <option value="pop">Pop</option>
      <option value="metal">Metal</option>
    </select>
  </form>
</template>

<script>
export default {
  name: "SelectDiscGenere",
  props: {
    genere: String,
  },
};
</script>

<style>
</style>