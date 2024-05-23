<template>
  <Login v-if="!logado" :logado="logado" :updateParentValue="updateParentValue" />
  <Internal v-if="logado" :logado="logado" :updateParentValue="updateParentValue" />
</template>

<script>
import Internal from "./components/Internal.vue"
import Login from "./components/Login.vue"


export default {
  name: 'App',
  components: { Internal, Login },
  data() {
    return {
      logado: false
    }
  },
  methods: {
    updateParentValue() {
      // Atualizando a propriedade 'value' no componente pai quando o evento é emitido pelo componente filho
      this.logado = !this.logado;
    },
  },
  computed: {
    //funcoes declaradas e usadas como se fosse campos
  },
  watch: {
    //observa alguma variavel a ser modificada 
  }
}

// ->beforeCreate
//criação ->created 
//->beforeMount
//montagem ->mounted
//atualização
//desmontagem
//this.$el ->pega o elemento raiz do component
//computed atualizar valor que depende de outro

</script>

<style>
html,
body {
  margin: 0;
  padding: 0
}

#app {
  height: 100%;
}
</style>
