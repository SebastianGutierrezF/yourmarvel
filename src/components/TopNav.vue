<script setup>
    import { ref } from 'vue';
    const searchInput = ref("");
    const botones = [
        {texto: 'Inicio', ruta: '#/inicio'},
        {texto: 'Personajes', ruta: '#/personajes'},
        {texto: 'Comics', ruta: '#/comics'},
    ];
    
</script>
<template>
    <div class="wrap">
        <a target="_blank" href="https://www.marvel.com/"><img src="../assets/logo.png" alt="marvel logo" class="logo"></a>
        <div class="menu">
            <a v-for="boton in botones" :href="boton.ruta" class="botonMenu">{{ boton.texto }}</a>
        </div>
        <div class="search">
            <i @click="$emit('search', searchInput); searchInput = ''"><span class="material-symbols-outlined">search</span></i>
            <input type="text" v-model="searchInput" @keyup.enter="$emit('search', searchInput); searchInput = ''">
        </div>
    </div>
</template>
<style scoped>
.wrap {
    display: flex;
    flex-flow: row nowrap;
    justify-content: space-between;
    align-items: center;
    width: 100vw;
    height: 50px;
    animation: blur-in 2s linear;
    background: transparent;
    border-bottom: 1px solid gray;
    z-index: 1;
    position: fixed;
    top: 0;
}
.wrap a {
    height: 100%;
}
.logo {
    height: 100%;
    object-fit: cover;
    border-right: solid 1px gray;
    border-left: solid 1px gray;
    margin-left: 40px;
    padding: 0px 30px;
}
.search {
    height: 100%;
}
.search input {
    margin-right: 10px;
    height: 100%;
    color: whitesmoke;
    width: 40px;
    border: none;
    transition: 500ms all;
    box-sizing: border-box;
    padding-right: 30px;
    background: transparent;
    border-left: solid gray 1px;
}
.search input:hover, input:focus {
    width: 200px;
}
.search i {
    position: absolute;
    right: 10px;
    top: 12px;
    cursor: pointer;
    color: red;
}
.menu {
    display: flex;
    flex-flow: row nowrap;
    gap: 50px;
    overflow-x: scroll;
}
.botonMenu {
    border-radius: 15px 0 15px 0;
    color: whitesmoke;
    width: 100px;
    height: 25px;
    text-align: center;
    font-style: normal;
    padding: 5px;
    box-sizing: content-box;
    font-weight: 400;
    cursor: pointer;
    transition: all 300ms;
    background: transparent;
    border: none;
    text-decoration: none;
}
.botonMenu:hover, .botonMenu:focus {
    background: red;
}
@keyframes blur-in {
    from {
        opacity: 0;
        filter: blur(100px);
    }
    to {
        opacity: 1;
        filter: blur(0px);
    }

}
@media (max-width: 800px) {
    .logo {
        border-left: none;
        margin-left: 0;
    }
}
</style>