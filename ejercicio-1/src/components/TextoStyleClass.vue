<template>
    <div>
        <p :class="{'texto-rojo':cambiaARojo}" :style="{fontSize:fontSize+'px'}" >{{ texto }}</p>
       
        <hr/>
        <label> Cambiar a Rojo</label>
        <input type="checkbox" v-model="cambiaARojo" >

        <input type="range" v-model="fontSize"  min="20" max="65">
    </div>
</template>

<script setup>
import { ref } from 'vue';


defineProps({
    texto: String
})
const cambiaARojo= ref(false);
const fontSize=ref(20);
</script>

<style  scoped>
p {
    color: green;
}
.texto-rojo{
    color:red;
}

</style>