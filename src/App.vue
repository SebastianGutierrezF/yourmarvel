<script setup>
import { ref, computed } from 'vue';
import Personajes from './components/Personajes.vue';
import Comics from './components/Comics.vue'
import TopNav from './components/TopNav.vue';
import Foot from './components/Footer.vue';
import Inicio from './components/Inicio.vue';

const searchInput = ref("");
const routes = {
  '/inicio': Inicio,
  '/personajes': Personajes,
  '/comics': Comics
}
const currentPath = ref(window.location.hash)

window.addEventListener('hashchange', () => {
  currentPath.value = window.location.hash
})

const currentView = computed(() => {
  console.log(window.location.hash);
  return routes[currentPath.value.slice(1) || '/'] || Personajes;
})
</script>

<template>
  <header>
    <TopNav @search="(i) => searchInput = i" />
  </header>
  <main>
      <div class="intro">
        <img src="./assets/intro.gif" alt="">
      </div>
      <component :is="currentView" :search-input="searchInput" />
  </main>
  <footer>
    <Foot/>
  </footer>
</template>

<style scoped>
.intro {
  width: 100vw;
  height: 100vh;
}

.intro img {
  width: 100%;
  height: 100%;
  animation: fade-out 1500ms cubic-bezier(1, -0.01, 1, .4);
  animation-iteration-count: 1;
  animation-fill-mode: forwards;
}

@keyframes fade-out {
  from {
    opacity: 1;
  }

  to {
    filter: blur(10px);
    opacity: 0;
  }
}

main {
  background: linear-gradient(rgba(52, 22, 29, 1) 28%, rgba(8, 1, 14, 1) 100%);
  overflow: hidden;
}
</style>
