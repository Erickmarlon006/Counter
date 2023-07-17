<template>
  <!--nav MENU DE NAVEGAÇÃO-->
  <!--aside CONTEÚDO LATERAL-->
  <main>
    <!--03.Utilizar o componente-->
    <MadCounter title="Counter"/>
  </main>
</template>

<script lang="ts">
import { defineComponent } from "vue";
//01.Importar o arquivo do componente
import MadCounter from "@/components/MadCounter.vue";

export default defineComponent({
  name: "MainView",
  //02.Listar os componentes
  components: {
    MadCounter,
  },
});
</script>
<style>
main{
  width: 100%;
}

</style>
