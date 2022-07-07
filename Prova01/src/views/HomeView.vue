<template>
    <Banner/>
    <div class="main-container">
        <h1>Monte seu Buguer:</h1>
        <FormBurger/>
    </div>
</template>

<script>
    import Banner from "../components/Banner.vue";
import FormBurger from "../components/FormBurger.vue";

    export default
    {
       name: "Home",
       components: 
       {
    Banner,
    FormBurger,
} 
    }

</script>

<style>
</style>