
<script setup></script>
<template>
    <section>
        <article>
            <h1>YourMarvel</h1>
            <h1>Para los fans verdaderos</h1>
            <br><br>
            <p>Lorem ipsum dolor sit amet, consectetur adipiscing elit. Aenean arcu sem, vulputate id condimentum et,
                sollicitudin vitae sem. Aenean at erat mattis, consequat leo vitae, auctor sem. Pellentesque et aliquam
                arcu. Donec aliquet tellus vel justo convallis, commodo interdum massa tempor. Aliquam erat volutpat.
            </p>
            <br><br>
            <a class="boton" href="#/personajes">¡Comienza aquí!</a>
        </article>
        <article>
            <img src="../assets/welcome.png" alt="">
        </article>
    </section>
</template>
<style scoped>
* {
    animation: blur-in 2s linear;
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
section {
    display: flex;
    flex-flow: row nowrap;
    justify-content: space-around;
    align-items: center;
    position: absolute;
    top: 50px;
    width: 100vw;
    height: 80vh;
}
section article:first-child {
    display: flex;
    flex-flow: column nowrap;
    align-items: center;
    max-width: 40%;
    z-index: 1;
}
h1 {
    color: whitesmoke;
    font-weight: 400;
    font-size: xx-large;
    align-self: flex-start;
}
h1:nth-child(2) {
    color: red;
}
p {
    color: whitesmoke;
}
section article img {
    height: 100%;
    position: absolute;
    right: 100px;
    bottom: 0px;
}
.boton {
    border-radius: 15px 0 15px 0;
    color: whitesmoke;
    width: 300px;
    height: 25px;
    text-align: center;
    font-style: normal;
    padding: 5px;
    box-sizing: content-box;
    font-weight: 400;
    font-size: large;
    cursor: pointer;
    transition: all 300ms;
    background: rgba(255, 0, 0, 0.678);
    border: none;
    text-decoration: none;
}
.boton:hover {
    background: rgba(255, 0, 0, 0.87);
    transform: scale(1.1);
}
</style>