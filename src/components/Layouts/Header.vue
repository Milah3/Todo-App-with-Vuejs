<template>
    <div>
    <header class="header">
        <h1> TodoList</h1>
    </header>

    <div id="nav">
        <router-link id="underline" to="/">Home</router-link> |
        <router-link id="underline" to="/about">About</router-link>
    </div>
    </div>
</template>

<script>
export default {
    name: "Header"
}
</script>

<style scoped>
    .header{
        background: #333;
        color: #fff;
        text-align: center;
        padding: 10px;
    }

    .header a {
        color: #fff;
        padding-right: 5px;
    }
    /* #underline{
        text-decoration: none;
    } */
</style>