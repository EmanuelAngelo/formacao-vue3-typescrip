import Cronometro from './Cronometro.vue';

<template>
  <Box>
    <div class="columns">
      <div class="column is-7">
        {{ tarefa.descricao || "Tarefa sem descrição" }}
      </div>
      <div class="column">
        <Cronometro :tempoEmSegundos="tarefa.duracaoEmSegundos" />
      </div>
    </div>
  </Box>
</template>

<script lang="ts">
import ITarefa from "@/interfaces/ITarefas";
import { defineComponent, PropType } from "vue";
import Box from "./Box.vue";
import Cronometro from "./Cronometro.vue";

export default defineComponent({
  name: "TareFa",
  components: { Cronometro, Box },
  props: {
    tarefa: {
      type: Object as PropType<ITarefa>,
      required: true,
    },
  },
});
</script>

<style scoped>
.box {
  background: #faf0ca;
}
</style>
