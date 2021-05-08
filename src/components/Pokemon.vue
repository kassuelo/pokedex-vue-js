<template>
  <div id="pokemon">
    <h1>{{ name | upper}}</h1> <!-- o pipe + nome do filtro faz aplicar um filtro ao valor da tag -->
    <small>{{ url }}</small>
  </div>
</template>

<script>
export default {
  props: {
    name: String,
    url: String,
  },
  filters: {
      upper: function(value){
          var newName = value[0].toUpperCase() + value.slice(1);
          return newName;
      }
  }
};
</script>

<style>
</style>