<template>
  <div :class="['page-wrapper', { 'dark-theme': isDark }]">
    <div class="theme-switch-wrapper">
      <button @click="toggleTheme" id="theme-toggle">
        {{ isDark ? '☀️ Modo Claro' : '🌙 Modo Oscuro' }}
      </button>
    </div>

    <div class="container">
      <header>
        <img src="/img/Aldo.jpeg" alt="perfil" />
        <h1>ING. Dorado Solano Aldo Aragon</h1>
        <p class="description">
          ¡Hola! Soy Aldo Aragon Dorado Solano, y actualmente estoy cursando la carrera de Ingeniería en Tecnologías de la Información y Comunicación. Siempre me ha fascinado la manera en que la tecnología mueve al mundo, esta carrera no ha sido tan fácil ya que en cada materia que cursé en esta carrera ha tenido sus obstáculos, pero esforzándose en cada reto que se ha presentado he logrado salir bien de cada una de mis materias.
          
          Me considero una persona muy enfocada; cuando realizo tareas o trabajos suelo apoyarme en la música para entrar en "zona de confort" y concentrarme al máximo en lo que estoy haciendo. Mi objetivo ahora mismo es cerrar esta etapa universitaria con los mejores resultados posibles, para así dar el salto al mundo laboral con bases sólidas. Busco integrarme a proyectos donde pueda aportar soluciones técnicas reales, seguir aprendiendo y, por supuesto, construir un camino profesional y económico estable para mi futuro.
        </p>
      </header>
    </div>
  </div>
</template>

<script setup>
import { ref, onMounted } from 'vue';

const isDark = ref(false);

const toggleTheme = () => {
  isDark.value = !isDark.value;
  // Guardamos la preferencia en localStorage
  localStorage.setItem('theme', isDark.value ? 'dark' : 'light');
};

onMounted(() => {
  // Al cargar el componente, verificamos si hay una preferencia guardada
  const savedTheme = localStorage.getItem('theme');
  if (savedTheme === 'dark') {
    isDark.value = true;
  }
});
</script>

<style scoped>
/* Variables aplicadas al contenedor principal del componente */
.page-wrapper {
  --bg-color: #ffffff;
  --text-color: #333333;
  --container-bg: #f9f9f9;
  --accent-color: #00d0ff;
  --btn-bg: #333;
  --btn-text: #fff;
  
  background-color: var(--bg-color);
  color: var(--text-color);
  font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
  min-height: 100vh;
  margin: 0;
  padding: 40px 20px;
  transition: background-color 0.3s, color 0.3s;
  display: flex;
  justify-content: center;
}

/* Colores cuando el modo oscuro está activo (clase .dark-theme) */
.dark-theme {
  --bg-color: #121212;
  --text-color: #e0e0e0;
  --container-bg: #1e1e1e;
  --accent-color: #4de1ff;
  --btn-bg: #f4f4f4;
  --btn-text: #121212;
}

.container {
  background-color: var(--container-bg);
  padding: 40px;
  border-radius: 15px;
  max-width: 800px;
  height: fit-content;
  box-shadow: 0 4px 15px rgba(0,0,0,0.1);
  transition: background-color 0.3s;
}

h1 {
  color: var(--accent-color);
  margin-top: 0;
}

.profile-img {
  width: 150px; /* Ajusta según necesites */
  border-radius: 50%;
  margin-bottom: 20px;
}

.description {
  line-height: 1.8;
  text-align: justify;
  white-space: pre-line;
}

.theme-switch-wrapper {
  position: fixed;
  top: 20px;
  right: 20px;
}

#theme-toggle {
  padding: 10px 20px;
  border: none;
  border-radius: 25px;
  background-color: var(--btn-bg);
  color: var(--btn-text);
  cursor: pointer;
  font-weight: bold;
  transition: transform 0.2s ease;
}

#theme-toggle:hover {
  transform: scale(1.05);
}
</style>