# 🧪 Ejercicio Práctico: El Alquimista de Vue

En este ejercicio, pondrás en práctica tus habilidades con los **Bindings Visuales** de Vue 3 (`:class` y `:style`). Tu misión es crear un panel de control para un alquimista que necesita gestionar sus pociones y su caldero.

## 🎯 Objetivos de Aprendizaje
- Implementar cambios de tema global usando `:class`.
- Gestionar estados de selección y categorías mediante objetos de clases.
- Manipular estilos complejos en tiempo real usando `:style` y `computed`.

---

## 📋 Instrucciones para el Alumno

### 1. Configuración Inicial
Crea un nuevo componente o limpia tu `App.vue`. Asegúrate de importar el CSS que se proporciona al final de este documento.

### 2. Tarea 1: Control de Iluminación (Theme Toggle)
- Crea una variable reactiva para controlar si el laboratorio está en modo "Noche".
- Implementa un botón que alterne este estado.
- Usa `:class` en el contenedor principal para aplicar la clase `.night-mode` cuando el estado sea activo.
- **Requisito**: El texto del botón debe cambiar dinámicamente ("Encender Luces" / "Apagar Luces").

### 3. Tarea 2: Inventario de Pociones
- Define una lista de al menos 3 pociones con propiedades como `id`, `nombre`, `tipo` (ej: 'curacion', 'veneno', 'energia') y `icono`.
- Al hacer clic en una poción, esta debe marcarse como "seleccionada".
- **Requisito**: Usa `:class` para aplicar:
    - Una clase basada en el `tipo` de poción (ej: `.potion-healing`, `.potion-poison`).
    - Una clase `.is-selected` solo si la poción es la actualmente seleccionada.

### 4. Tarea 3: El Caldero Maestro
- Crea tres controles (inputs):
    1. Un Color Picker para el color del líquido.
    2. Un Range (Deslizador) para el tamaño del caldero (100px a 300px).
    3. Un Range para la "intensidad del fuego" (rotación o brillo).
- **Requisito**: Crea una propiedad computada (`computed`) que devuelva un objeto de estilos y aplícala al elemento del caldero usando `:style`.

---

## 🎨 Código CSS Proporcionado

Copia y pega este código en tu archivo `style.css` o en un bloque `<style>`:

```css
@import url('https://fonts.googleapis.com/css2?family=Cinzel:wght@400;700&family=Quicksand:wght@300;500;700&display=swap');

:root {
  --bg-lab: #fdf6e3;
  --text-lab: #2c3e50;
  --accent: #8e44ad;
  --border: #dcdde1;
  --card: #ffffff;
  --transition: all 0.4s cubic-bezier(0.4, 0, 0.2, 1);
}

.night-mode {
  --bg-lab: #1a1a2e;
  --text-lab: #e9e9e9;
  --accent: #e94560;
  --border: #444;
  --card: #16213e;
}

body {
  margin: 0;
  font-family: 'Quicksand', sans-serif;
  background-color: var(--bg-lab);
  color: var(--text-lab);
  transition: var(--transition);
}

.lab-container {
  max-width: 900px;
  margin: 0 auto;
  padding: 2rem;
}

h1, h2 {
  font-family: 'Cinzel', serif;
  text-align: center;
}

section {
  background: var(--card);
  border-radius: 1rem;
  padding: 1.5rem;
  margin-bottom: 2rem;
  border: 2px solid var(--border);
  box-shadow: 0 10px 20px rgba(0,0,0,0.1);
}

/* Estilos para Tarea 2 */
.potion-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(150px, 1fr));
  gap: 1rem;
  margin-top: 1rem;
}

.potion-item {
  padding: 1rem;
  border-radius: 0.5rem;
  text-align: center;
  cursor: pointer;
  border: 2px solid transparent;
  transition: var(--transition);
  background: rgba(0,0,0,0.05);
}

.is-selected {
  border-color: var(--accent);
  transform: translateY(-5px);
  box-shadow: 0 5px 15px rgba(0,0,0,0.2);
}

/* Colores por tipo */
.potion-healing { color: #27ae60; background: rgba(39, 174, 96, 0.1); }
.potion-poison { color: #c0392b; background: rgba(192, 57, 43, 0.1); }
.potion-energy { color: #f1c40f; background: rgba(241, 196, 15, 0.1); }

/* Estilos para Tarea 3 */
.cauldron-box {
  display: flex;
  gap: 2rem;
  align-items: center;
}

.cauldron-preview {
  display: flex;
  align-items: center;
  justify-content: center;
  border-radius: 50% 50% 40% 40%;
  border: 4px solid #333;
  margin: 0 auto;
}

.controls-group {
  display: flex;
  flex-direction: column;
  gap: 1rem;
  flex: 1;
}

.btn {
  display: block;
  margin: 0 auto 1rem;
  padding: 0.8rem 1.5rem;
  border-radius: 2rem;
  border: none;
  background: var(--accent);
  color: white;
  font-weight: bold;
  cursor: pointer;
  transition: var(--transition);
}

.btn:hover {
  filter: brightness(1.2);
  transform: scale(1.05);
}
```

## 💡 Tips
- Recuerda que `:class` puede recibir un objeto `{ 'nombre-clase': condicion }`.
- Para la Tarea 3, el objeto de estilos en tu `computed` debe tener las claves en **camelCase** (ej: `backgroundColor` en lugar de `background-color`).
- ¡No olvides usar `v-model` para vincular tus inputs con tus variables reactivas!
