<template>
    <h1>{{title}}</h1>
</template>

<script>
    export default{
        props:['title']
    }
</script>

<style scoped>
*{
    background-color: indigo;
    height: 4.2rem;
}
h1{
    text-align: center;
    color: azure;
    margin: 0;
    padding-top: 1rem;
}
</style>
