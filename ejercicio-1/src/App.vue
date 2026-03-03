<script setup>
import ComponenteCualquiera from './components/ComponenteCualquiera.vue';
import TextoStyleClass from './components/TextoStyleClass.vue';



</script>

<template>
  <p>Este es un texto que esta fuera del componente de TextoStyleClass</p>
  <div> 
   <TextoStyleClass texto="Hola Mundo"/>
  </div>
  <br>
  <ComponenteCualquiera/>
</template>

<style scoped>
p{
  color:blueviolet;
}


</style>
