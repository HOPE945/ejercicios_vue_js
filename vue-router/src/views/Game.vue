<template>
  <h1>Estamos en el Juego</h1>
  <button @click="load">Cargar</button>
</template>

<script>
import { useRoute, useRouter } from "vue-router";

export default {
  setup() {
    const route = useRoute();
    const router = useRouter();
    console.log(router);

    const load = () => {
      console.log("Ejecutando peticion");
      setTimeout(() => {
        console.log("Volver a la home");
        router.push("/");
      }, 3000);
    };
    return {
      load,
    };
  },
};
</script>

<style></style>
