<template>
    <NavBar :logo="logo_src" :alt="desc_src"/>
    <RouterView />
    <Footer></Footer>
</template>

<script>
import { RouterLink, RouterView } from 'vue-router'
import NavBar from './components/NavBar.vue';
import Footer from "./components/Footer.vue"

  export default
  {
    name: "App",
    components:
    {
      RouterView,
      RouterLink,
      NavBar,
      Footer,
    },
    data()
    {
      return{
        logo_src: "/img/logo.png",
        desc_src: "Make Your Burguer!"
      }
    },
  }
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Poppins:ital,wght@0,100;0,200;0,300;0,400;0,500;0,600;0,700;0,800;0,900;1,100;1,200;1,300;1,400;1,500;1,600;1,700;1,800;1,900&display=swap');

  *
  {
    font-family: 'Poppins', sans-serif;
    margin: 0;
    padding: 0;
    box-sizing: border-box;
  }
  ::-webkit-scrollbar
  {
    display: none;
  }
  body
  {
    height: 100vh;
    width: 100vw;
    text-rendering: optimizeLegibility;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
  }
  .main-container
  {
    margin: 50px 10px;
    min-height: 95%;
  }

  h1
  {
    text-align: center;
    text-transform: uppercase;
    font-size: 42px;
    margin-bottom: 30px;
    color: #222;
  }

</style>
