<template>
  <div class="main-container">
    <h1>Gerenciador de Pedidos:</h1>
    <Dashboard/>
  </div>
</template>

<script>
  import Dashboard from '../components/Dashboard.vue'

  export default
  {
    name: "Pedidos",
    components:
    {
      Dashboard,
    }
  }
</script>

<style>
</style>
