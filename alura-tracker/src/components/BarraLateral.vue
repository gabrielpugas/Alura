<template>
  <header>
    <h1>
      <img src="../assets/logo.png" alt="Logo do Alura Tracker">
    </h1>
    <button class="button" @click="alterarTema">
      <span class="icon">
        <i class="fa-solid fa-circle-half-stroke"></i>
      </span>
      <p>{{ textoBotao }}</p>
    </button>
  </header>
</template>

<script lang="ts">
import { defineComponent } from 'vue';

export default defineComponent({
  name: "BarraLateral",
  data() {
    return {
      modoEscuroAtivo: false
    }
  },
  emits: ["aoTemaAlterado"],
  computed:{
    textoBotao () {
      if(this.modoEscuroAtivo)
        return "Desativar Modo Escuro"
      return "Ativar Modo Escuro"
    }
  },
  methods: {
    alterarTema () : void {
      this.modoEscuroAtivo = !this.modoEscuroAtivo
      this.$emit("aoTemaAlterado",this.modoEscuroAtivo)
    }
  }
})
</script>

<style>
header {
  padding: 1rem;
  display: flex;
  flex-direction: column;
  align-items: center;
  background: #0d3b66;
  width: 100%;
  height: 100vh;
}

@media only screen and (max-width: 768px) {
  header {
    padding: 2.5rem;
    height: auto;
  }
}
</style>

<style scoped>
.button {
  background-color: var(--bg-primario);
  color: var(--texto-primario);
}
</style>