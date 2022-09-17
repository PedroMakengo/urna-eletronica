<template>
  <div class="urna-tela">
    <div v-if="tela != 'fim'" class="urna-tela-voto">votação</div>
    <div v-if="tela == 'fim'" class="urna-tela-fim">finalização</div>
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";

export default defineComponent({
  name: "Tela",
  props: {
    tela: { type: String },
  },
});
</script>

<style scoped>
.urna-tela {
  width: 55%;
  height: 100%;

  background-color: var(--ballot-box-screen-color);
  border-radius: 5px;
  border: 2px solid var(--light-border-color);
  padding: 20px;
  color: var(--dark-text-color);
}
</style>
