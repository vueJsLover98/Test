<template>
    <li>
        <base-card>
            <header>
                <h3>{{title}}</h3>
                <base-button @click="deleteData(id)" mode="flat">Delete</base-button>
            </header>
            <p>{{description}}</p>
            <nav>
                <a :href="link">View Resource</a>
            </nav>
        </base-card>
    </li>
</template>

<script>
    export default{
        inject:['deleteData'],
        props:['title', 'description', 'link', 'id'],

    }
</script>

<style scoped>
li{
    margin-top: 1.5rem;
    margin-bottom: 1.5rem;
    display: block;
}
header{
    display: flex;
    justify-content: space-between;
    align-items: center;
}

p{
    margin: 0.5rem, 0;
}

nav{
    margin: 0.5rem, 0;
}
</style>

