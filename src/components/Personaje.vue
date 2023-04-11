<script>
export default {
    name: "Personaje",
    props: {
        name: {
            type: String,
            required: true
        },
        description: {
            type: String,
            required: true
        },
        thumbnail: {
            type: String,
            required: true
        }
    }
}
</script>

<template>
    <div class="tarjeta">
        <h1>{{ name }}</h1>
        <br>
        <img :src="thumbnail" alt="">
        <br>
        <br>
        <h4>{{ description }}</h4>
    </div>
</template>

<style scoped>
.tarjeta {
    width: 300px;
    color: whitesmoke;
    padding: 10px;
    box-sizing: border-box;
}
.tarjeta img {
    height: 200px;
    object-fit: cover;
    border-radius: 50px;
}
h1 {
    font-family: 'Montserrat Alternates', sans-serif;
    font-weight: 400;
}
</style>