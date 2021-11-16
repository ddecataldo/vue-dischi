<template>
    <main>
        <div class="container">
            <div class="row row-cols-1 row-cols-md-5 g-4 py-5">
                <div
                class="col"
                v-for="(album, i) in albumList"
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

export default {
    name: "ContainerAlbum",
    components: {
        CardAlbum,
    },
      data() {
        return {
            urlApi: "https://flynn.boolean.careers/exercises/api/array/music",
            albumList: [],
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
    },
    mounted(){
        this.fetchData();
    }
}

</script>

<style>

</style>