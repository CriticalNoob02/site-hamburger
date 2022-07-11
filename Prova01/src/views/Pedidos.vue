<template>
  <div class="main-container">
    <h1>Gerenciador de Pedidos:</h1>
    <Dashboard2/>
  </div>
</template>

<script>
  import Dashboard2 from '../components/Dashboard2.vue'

  export default
  {
    name: "Pedidos",
    components:
    {
      Dashboard2,
    }
  }
</script>

<style>
</style>
