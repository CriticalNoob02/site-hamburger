<template>
    <div class="mainBanner">
        <h1>Burger Banner</h1>
    </div>
</template>

<script>
    export default
    {
        name: "Banner"
    }
</script>

<style scoped>
     .mainBanner
     {
        background: url(../../public/img/burger.jpg);
        background-position: 0 -150px;
        background-size: cover;
        background-repeat: no-repeat;
        background-attachment: fixed;
        height: 650px;
        display: flex;
        align-items: center;
        justify-content: flex-start;
     }
     .mainBanner h1
     {
        color: #F0F2F2;
        text-align: center;
        font-size: 3.125rem;
        padding: 15px 35px;
        box-shadow: 0 10px 15px rgba(0, 0, 0, 0.5);
     }
    @media (max-width: 1250px)
    {
        .mainBanner
        {
            background-position: 0 0;
        }
    }
    @media (max-width: 700px)
    {
        .mainBanner h1
        {
            font-size: 2.813rem;
            padding: 10px 15px;
        }
    }
     @media (max-width: 560px)
    {
        .mainBanner 
        {
            justify-content: center;
        }
    }
    @media (max-width: 470px)
    {
        .mainBanner
        {
            height: 550px;
            background-position: 0 -150px;
        }
        .mainBanner h1
        {
            font-size: 2.188rem;
            padding: 5px 5px;
        }
    }
</style>