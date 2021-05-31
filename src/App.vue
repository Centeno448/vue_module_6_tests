<template>
  <h1>Bienvenido al curso de Vue</h1>
  <div class="notas">
    <nav>
      <p v-if="!notas.length">No hay notas guardadas</p>
      <ul v-if="notas.length">
        <li v-for="nota in notas" :key="nota.titulo">
          <button
            @click="notaActual = nota"
            :class="{ active: nota === notaActual }"
          >
            {{ nota.titulo }}
          </button>
        </li>
      </ul>
    </nav>
    <div v-if="notaActual" class="current-note">
      <h2>{{ notaActual.titulo }}</h2>

      <textarea v-model="notaActual.contenido"></textarea>
    </div>
  </div>
</template>

<script>
export default {
  name: "App",
  data: function() {
    return {
      notas: [{ titulo: "titulo", contenido: "contenido" }],

      notaActual: null,
    };
  },
};
</script>

<style scoped>
body {
  padding: 20px 30px;
}
h1 {
  display: inline-block;
  margin-right: 20px;
}
.create-new-button {
  position: relative;
  top: -10px;
}
nav ul {
  list-style-type: none;
}
nav button,
nav button:hover,
nav button:active,
nav button:focus {
  background: none;
  color: #606c76;
}
nav button {
  display: block;
  width: 100%;
  border: none;
  padding: 0 10px;
  font-size: 18px;
  font-weight: normal;
  text-transform: none;
  text-align: left;
}
nav button:hover {
  text-decoration: underline;
}
nav button.active {
  background: gray;
  color: white;
}
.notes {
  display: flex;
}
nav {
  flex: 0 0 calc(33% - 20px);
  margin-right: 20px;
}
.current-note {
  flex: 1;
}
.current-note input,
.current-note textarea {
  color: #606c76;
  border: none;
  border-radius: 0;
  padding: 5px;
}
.current-note input:hover,
.current-note textarea:hover,
.current-note input:focus,
.current-note textarea:focus {
  background: lavender;
}
.current-note input {
  font-size: 3.6rem;
  line-height: 1.25;
  font-weight: 300;
  letter-spacing: -0.1rem;
  margin-bottom: 2rem;
  margin-top: 0;
}
.current-note textarea {
  font-size: 18px;
  color: #606c76;
}
</style>
