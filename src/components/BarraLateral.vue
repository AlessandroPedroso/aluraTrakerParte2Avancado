<template>
  <header>
    <h1>
      <img src="../assets/logo.png" alt="imagem da alura traker" />
    </h1>
    <div class="has-text-centered mt-5">
      <button class="button" @click="alterarTema">{{ textoBotao }}</button>
    </div>
    <nav class="panel mt-5">
      <ul>
        <li>
          <router-link to="/" class="link">
              <i class="fas fa-tasks"></i>
              Tarefas
          </router-link>
        </li>
        <li>
          <router-link to="/projetos" class="link">
              <i class="fas fa-project-diagram"></i>
              Projetos
          </router-link>
        </li>
      </ul>
    </nav>
  </header>
</template>

<script lang="ts">
import { defineComponent } from "vue";

export default defineComponent({
  name: "BarraLateral",
  emits: ["aoTemaAlterado"],
  data() {
    return {
      modoEscuroAtivo: false,
    };
  },
  computed:{
    textoBotao(){
        if(this.modoEscuroAtivo){
        return 'Desativar modo escuro'
     }
     return 'Ativar modo escurso'
    }

  },
  methods: {
    alterarTema() {
      this.modoEscuroAtivo = !this.modoEscuroAtivo;
      this.$emit("aoTemaAlterado", this.modoEscuroAtivo);
    },
  },
});
</script>

<style scoped>
h1 {
  display: flex;
  justify-content: center;
}
header {
  padding: 1rem;
  background: #0d3b66;
  width: 100%;
  height: 100vh;
  text-align: center;
}

.link{
  color: #fff;
}

.link:hover{
  color: #faf0ca;
}

.link.router-link-active{
  color:#faf0ca;
}

@media only screen and (max-width: 768px) {
  header {
    padding: 2.5rem;
    height: auto;
  }
}
</style>
