<template>
  <div>
    <section>
      <strong class="display">
        {{ tempoDecorrido }}
      </strong>
    </section>
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";

export default defineComponent({
  name: "CroNometro",
  props: {
    tempoEmSegundos: {
      type: Number,
      default: 0,
    },
  },
  computed: {
    tempoDecorrido(): string {
      return new Date(this.tempoEmSegundos * 1000).toISOString().substr(11, 8);
    },
  },
});
</script>
<style>
.display {
  color: var(--texto-primario);
}
</style>
