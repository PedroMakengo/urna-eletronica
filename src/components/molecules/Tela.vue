<template>
  <div class="urna-tela"></div>
</template>

<script lang="ts">
import { defineComponent } from "vue";

export default defineComponent({
  name: "Tela",
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
