<template>
      <nav class="nav">
        <RouterLink to="/">
            <img :src="logo" :alt="desc" id="logo">
        </RouterLink>
        <div id="nav">
            <RouterLink to="/">Home</RouterLink>
            <RouterLink to="/pedidos">Pedidos</RouterLink>
        </div>
      </nav>
</template>

<script>
    export default
    {
        name: "NavBar",
        props:["logo", "desc"]
    }
</script>

<style scoped>
    nav
    {
        /* position: fixed; */
        width: 100vw;
        height: 10vh;
        background-color: #222;
        box-shadow: 0 0 25px rgba(0, 0, 0, 0.9);
        padding: 15px 50px;
        display: flex;
        justify-content: space-between;
        align-items: center;
    }
    #logo
    {
        width: 50px;
        height:50px;
    }
    nav a
    {
        color: #FCBA03;
        text-decoration: none;
        margin: 15px;
        transition: 0.3s;
    }

    nav a:hover
    {
        color: aliceblue;

    }
        @media (max-width: 900px)
    {
        nav
        {
            padding: 10px 10px
        }
        nav a
        {
            font-size: 1.25rem;
        }
    }


</style>