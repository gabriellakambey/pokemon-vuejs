<template>
  <div class="search">
      <b-nav-form>
          <b-form-input size="md" class="mr-md-2" placeholder="Search Pokemon"></b-form-input>
          <b-button size="md" class="my-2 my-md-0" type="submit">Search</b-button>
      </b-nav-form>
  </div>
</template>

<script>
export default {
    name: 'SearchPokemon'
}
</script>

<style>
.search {
    padding-top: 70px;
    padding-bottom: 50px;
    justify-content: center;
    text-align: center;
    align-items: center;
}
</style>