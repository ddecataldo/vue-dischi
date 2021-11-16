<template>
    
    <div class="card h-100">
        <img :src="src" class="card-img-top" alt="...">
        <div class="card-body">
            <h5 class="card-title">{{ title }}</h5>
            <div class="card-text">
                <p class="card-descrption">{{ description }}</p>
                <p class="card-data">{{ data }}</p>
            </div>
        </div>
    </div>
        
</template>

<script>
export default {
    name: "CardAlbum",
    props: {
        src: String,
        title: String,
        description: String,
        data: String,
    },
    data() {
        return {};
    },
}
</script>

<style>

</style>