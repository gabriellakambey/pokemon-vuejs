<template>
<div class="list">
  <article><h5>{{ pokemon.name }}</h5></article>
  <!-- <div class="card">
    <h5>{{ pokemon.name }}</h5>
  </div> -->
</div>
</template>

<script>

export default {
    name:'ListPokemon',
    props: ["pokemon"]
}
</script>

<style>
.list{
  display: flex;
  justify-content: center;
  align-items: center;
  width: 100%;
}

article {
background-color:rgb(255, 255, 255);
  width: 200px;
  box-shadow: 0 4px 8px 0 rgba(0, 0, 0, 0.2);
  transition: 0.3;
  border: 2px solid grey;
  border-radius: 10px;
  padding: 20px;
  margin: 10px;
  cursor: pointer;
}
  
</style>