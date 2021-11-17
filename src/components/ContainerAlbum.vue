<template>
    <main>
        <div class="container">

            <div class="row">
                <div class="col-md-12">
                    
                    <Select @inizioRicerca="filtroGenere"></Select>

                </div>
            </div>

            <div class="row row-cols-1 row-cols-md-5 g-4 py-5">
                <div
                    class="col"
                    v-for="(album, i) in listaAlbumFiltrati"
                    :key="i"
                >
                <CardAlbum
                    :src="album.poster"
                    :title="album.title"
                    :description="album.author"
                    :data="album.year"
                ></CardAlbum>
                </div>
            </div>
        </div>
    </main>

</template>

<script>
import axios from "axios";
import CardAlbum from "./CardAlbum.vue";
import Select from "./Select.vue";

export default {
    name: "ContainerAlbum",
    components: {
        CardAlbum,
        Select,
    },
      data() {
        return {
            urlApi: "https://flynn.boolean.careers/exercises/api/array/music",
            albumList: [],
            genereScelto: "",
        };
    },
    methods: {
        fetchData() {

            axios.get(this.urlApi).then((ajaxResponse) =>  {
                /* const albumGenerate = ajaxResponse.data;
                this.albumList.push(albumGenerate.response); */
                this.albumList = ajaxResponse.data.response;
            });

        },
        filtroGenere(genereDigitato) {
            this.genereScelto = genereDigitato;
            /* console.log(genereDigitato); */
        },
    },
    mounted(){
        this.fetchData();
    },
    computed: {
        listaAlbumFiltrati() {

            if (!this.genereScelto) {
                return this.albumList;
            }

            return this.albumList.filter(elemento => {
                return elemento.genre.toLowerCase().includes(this.genereScelto.toLowerCase())
            });
            
            },
        },
    }

</script>

<style>

</style>