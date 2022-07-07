<template>
    <footer>
        <div>
            <p>Criado por <a href="https://github.com/CriticalNoob02" target="_blank">CriticalNoob02</a></p>
            <div class="imgBox"></div>
        </div>
    </footer>
</template>

<script>
    export default
    {
        name: "Footer",
    }
</script>

<style scoped>

footer
{
    height: 10vh;
    background-color: #222;

}

footer div
{
    display: flex;
    justify-content: center;
    align-items: center;
    width: 100%;
    padding: 15px;
    margin-bottom: 0;
    border-top: 1px solid rgba(0, 0, 0, 0.1);
    text-align: center;
}

footer div p
{
    color: #999;
}

footer div a
{
    color: #FCBA03;
    text-decoration: none;
    font-weight: 500;
}

footer div .imgBox
{
    width: 2vw;
    height: 2vh;
    background: url(../../public/img/Selo.png);
    background-size: cover;
    background-position: center;
    border: none;

}
</style>