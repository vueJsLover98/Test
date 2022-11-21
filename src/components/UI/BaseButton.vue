<template>
    <button :class="mode">
        <slot></slot>
    </button>
</template>

<script>
export default {
    props:['mode']
}
</script>

<style scoped>
button{
    border: 0;
    padding: 0.5rem 1rem ;
    cursor: pointer;
    color: black;
}

button:hover,
button:active {
  background-color: #450072;
  border-color: #510086;
}

.flat {
  background-color: transparent;
  border: none;
}

.flat:hover,
.flat:active {
  background-color: #edd2ff;
}

</style>