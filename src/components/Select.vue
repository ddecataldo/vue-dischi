<template>

    <div class="input-group mt-5">
        
        <select class="form-select" aria-label="Default select example"
        v-model="genereUtente"
        @keydown.enter="avviaRicerca">
            <option value="">Tutti</option>
            <option value="rock">Rock</option>
            <option value="metal">Metal</option>
            <option value="pop">Pop</option>
            <option value="jazz">Jazz</option>
        </select>

        <button class="btn btn-outline-primary" type="button"
        @click="avviaRicerca"
        >Ricerca</button>

    </div>

    
</template>

<script>
export default {
    name: "BarraDiRicerca",
    data(){
        return{
            genereUtente:"",
        };
    },
    methods:{
        avviaRicerca(){
            this.$emit("inizioRicerca", this.genereUtente);
        },
    }
     
    
}
</script>