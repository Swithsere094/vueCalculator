<script>
import calculadoraComponent from "./components/calculadoraComponent.vue"

  export default {
    components: {
      calculadoraComponent
    },
    setup(){

      return {

      }
    }
  }
</script>

<template>
  <main>
    <calculadoraComponent />
  </main>
</template>

<style scoped>
  main {
    display: flex;
    width: 100vw;
    height: 100vh;
    align-items: center;
    justify-content: center;
  }
</style>
