<template>
  <div class="box">
    <div class="columns">
      <div
        class="column is-8"
        role="form"
        aria-label="Formulário para criação de uma nova tarefa"
      >
        <input
          type="text"
          class="input"
          placeholder="Qual tarefa você deseja iniciar?"
          v-model="descricao"
        />
      </div>
      <div class="column">
        <TemporiZador @aoTemporizadorFinalizado="finalizarTerefa" />
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";
import TemporiZador from "./Temporizador.vue";
export default defineComponent({
  name: "FormuLário",
  emits: ["aoSalvarTarefa"],
  components: { TemporiZador },
  data() {
    return {
      descricao: "",
    };
  },
  methods: {
    finalizarTerefa(tempoDecorrido: number): void {
      this.$emit("aoSalvarTarefa", {
        duracaoEmSegundos: tempoDecorrido,
        descricao: this.descricao,
      });
      this.descricao = "";
    },
  },
});
</script>
