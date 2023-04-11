<script>
export default {
    name: "Footer"
}
</script>
<template>
    <div class="wrap">
        <a target="_blank" href="https://www.linkedin.com/in/sebastian-gutierrez-fernandez-85837b150/">
            <img src="../assets/namLogo.png" alt="">
        </a>
        <h5>Made by Sebastián Gutiérrez @ 2023</h5>
        <a href="mailto:sebask811@gmail.com"><p>Contact me</p></a>
    </div>
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
.wrap {
    display: flex;
    flex-flow: row wrap;
    justify-content: space-between;
    align-items: center;
    padding: 0 20px;
    box-sizing: border-box;
    width: 100%;
    height: 80px;
    position: absolute;
    bottom: 0px;
    color: whitesmoke;
    background: transparent;
    border-top: solid gray 1px;
}
.wrap a img {
    height: 70px;
}
.wrap a {
    text-decoration: none;
}
.wrap p, h5 {
    color: whitesmoke;
    font-weight: 300;
    transition: all 500ms;
}
.wrap p:hover {
    transform: translate(-10px);
}
</style>