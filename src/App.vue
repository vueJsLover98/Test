<template>
    <the-header title="RememberMe"></the-header>
    <the-resource></the-resource>
</template>

<script>
  import TheHeader from "./components/layout/TheHeader.vue";
  import TheResource from "./components/learning-resources/TheResource.vue";
  
  export default{
    components:{
      TheHeader,
      TheResource,
    }
  }

</script>

<style>
  * {
    box-sizing: border-box;
  }

  html {
    font-family: 'Roboto', sans-serif;
    font-size: large;
  }

  body {
    margin: 0;
    position: static;
  }
</style>
