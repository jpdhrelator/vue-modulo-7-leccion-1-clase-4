<script setup>
import { computed, ref } from 'vue';



const isDark = ref(false)
const boxSize = ref(150);
const fontSize = ref(16);
const borderRadius= ref(16);
const boxColor=ref('#6366f1');
const isAnimated = ref(true);

const boxStyles= computed(()=>{
  return {
    width: `${boxSize.value}px`,
    height: `${boxSize.value}px`,
    fontSize:`${fontSize.value}px`,
    backgroundColor: boxColor.value,
    borderRadius: `${borderRadius.value}%`,
    boxShadow: isAnimated.value ? `0 0 20px ${boxColor.value}80` : 'none',
    transition: 'all 0.4s ease'
  }
});

const toggleTheme= ()=>{
  isDark.value = !isDark.value;
   document.body.classList.toggle('dark-theme', isDark.value);
}

const activeStatus = ref('success')
const statuses = [
  { id: 'success', label: 'Operación Exitosa', icon: '✅' },
  { id: 'warning', label: 'Requiere Atención', icon: '⚠️' },
  { id: 'error', label: 'Error Irrecuperable', icon: '❌' }
]

const getCardClass = (statusId) => {
  return {
    'status-card': true,
    'is-success': statusId === 'success',
    'is-warning': statusId === 'warning',
    'is-error': statusId === 'error',
    'is-selected': activeStatus.value === statusId
  }
}
</script>

<template>
  <div class="app-container" >
   <header>
      <h1>Vue Visual Bindings</h1>
      <p class="subtitle">Dominando :class y :style  </p>
    </header>
    <section>
      <h2>🌓 Cambio de Tema (Class Binding)</h2>
      <p style="margin-bottom: 1rem;">
        Usa <code>:class="{ 'dark-theme': isDark }" </code> para modificar el aspecto global.
      </p>
      <button class="btn btn-primary" @click="toggleTheme">
        Cambiar a modo {{ isDark ? 'Claro' : 'Oscuro' }}
      </button>
    </section>
    <section>
      <h2>🧪 Laboratorio de Estilos (Inline Style Binding)</h2>
      <div class="playground-area">
        <div class="controls">
          <div class="control-group">
            <label>Tamaño Letra: {{ fontSize }}px</label>
            <input type="range" v-model="fontSize" min="16" max="30">
          </div>
           <div class="control-group">
            <label>Tamaño: {{ boxSize }}px</label>
            <input type="range" v-model="boxSize" min="88" max="250">
          </div>
          <div class="control-group">
            <label>Radio de Borde: {{ borderRadius }}%</label>
            <input type="range" v-model="borderRadius" min="0" max="50">
          </div>
           <div class="control-group">
            <label>Color de fondo</label>
            <input type="color" v-model="boxColor">
          </div>
          <div class="control-group">
            <label>
              <input type="checkbox" v-model="isAnimated"> Activar Brillo Dinámico
            </label>
          </div>
        </div>
        <div class="preview">
          <div class="preview-box" :style="boxStyles"> ELEMENTO</div>
        </div>
      </div>
    </section>
    <section>
      <h2>🏷️ Estados Dinámicos (Clases Reactivas)</h2>
      <div class="status-grid">
    
        <div 
          v-for="status in statuses" 
          :key="status.id"
          :class="getCardClass(status.id)"
          @click="activeStatus = status.id"
        >
          <span style="font-size: 2rem;">{{ status.icon }}</span>
          <h3 style="margin-top: 1rem;">{{ status.label }}</h3>
        </div>
      </div>

    </section>
  </div>

</template>


