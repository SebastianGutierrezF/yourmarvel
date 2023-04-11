<script>
import Personaje from './Personaje.vue';
import axios from 'axios';
export default {
    data() {
        return {
            personajes: [],
            apiKey: "c448b1c45bec3c1d246230a1501cde50",
            offset: 0,
            mounted: false,
            networkError: false
        }
    },
    mounted() {
        this.getPersonajes();
    },
    props: {
        searchInput: {
            type: String,
            required: false
        }
    },
    watch: {
        searchInput: function () { this.searchPersonaje() }
    },
    name: "Personajes",
    components: {
        Personaje
    },
    methods: {
        getPersonajes() {
            axios.get('https://gateway.marvel.com/v1/public/characters', { params: { "apikey": this.apiKey, "offset": this.offset } })
                .then(response => {
                    this.personajes = response.data.data.results;
                    this.networkError = false;
                    this.mounted = true;
                })
                .catch(err => {
                    if (err == "AxiosError: Network Error") {
                        this.networkError = true;
                    } else {
                        alert("Ocurrio un error al realizar la consulta: " + err);
                    }
                })
        },
        searchPersonaje() {
            axios.get('https://gateway.marvel.com/v1/public/characters', { params: { "apikey": this.apiKey, "name": this.searchInput } })
                .then(response => {
                    this.personajes = response.data.data.results;
                    this.networkError = false;
                }).catch(err => {
                    if (err == "AxiosError: Network Error") {
                        this.networkError = true;
                    } else {
                        alert("Ocurrio un error al realizar la consulta: " + err);
                    }
                });
        },
        prevResults() {
            this.offset -= 20;
            this.getPersonajes();
        },
        nextResults() {
            this.offset += 20;
            this.getPersonajes();
        }
    }
}
</script>

<template>
    <div class="noResults" v-if="mounted && personajes.length == 0 && !networkError">
        <h1>
            No se encontraron personajes.
        </h1>
        <img src="../assets/groot.png" alt="">
    </div>
    <div class="noResults" v-if="networkError">
        <h1>
            No pareces tener conexión a internet.
        </h1>
        <img src="../assets/groot.png" alt="">
    </div>
    <section class="tarjetas" v-if="!networkError">
        <Personaje v-for="personaje in personajes" :name="personaje.name" :description="personaje.description"
            :thumbnail="personaje.thumbnail.path + '/standard_fantastic.jpg'" />
    </section>
    <div class="paginacion">
        <button @click="prevResults" :disabled="offset == 0">
            <span class="material-symbols-rounded">
                arrow_back
            </span>
        </button>
        <button @click="nextResults">
            <span class="material-symbols-rounded">
                arrow_forward
            </span>
        </button>
    </div>
</template>

<style scoped>
.tarjetas {
    display: flex;
    flex-flow: row wrap;
    justify-content: space-evenly;
    align-items: start;
    gap: 20px;
    width: 100%;
    top: 50px;
    height: calc(100vh - 180px);
    position: absolute;
    padding: 20px;
    overflow: scroll;
    box-sizing: border-box;
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
.paginacion {
    width: 100%;
    border-top: solid 1px gray;
    height: 50px;
    display: flex;
    justify-content: space-between;
    position: absolute;
    bottom: 80px;
    padding: 0 50px;
    box-sizing: border-box;
    animation: blur-in 2s linear;
}

.paginacion button {
    background: transparent;
    border: none;
    color: whitesmoke;
    cursor: pointer;
}

.noResults h1 {
    position: absolute;
    top: 200px;
    color: whitesmoke;
    left: 50%;
    transform: translate(-50%);
    text-align: center;
    animation: blur-in 2s linear;
    z-index: 1;
}

.noResults img {
    position: absolute;
    height: 400px;
    width: auto;
    bottom: 130px;
    right: 50px;
    animation: blur-in 2s linear;
}
</style>