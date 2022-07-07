<template>
    <div class="messageContent">
        <p>{{ msg }}</p>
    </div>
</template>

<script>
    export default
    {
        name: "Message",
        props:
        {
            msg: String
        }
    }
</script>

<style scoped>
    .messageContent
    {
        text-align: center;
        color: #004085;
        background-color: #CCE5FF;
        border: 2px solid #88DAFF;
        border-radius: 10px;
        padding: 10px;
        width: 45vw;
        margin: 30px auto;
    }
</style>