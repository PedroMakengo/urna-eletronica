<template>
  <div class="urna">
    <Tela />
    <Teclado />
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";
import Teclado from "@/components/molecules/Teclado.vue";
import Tela from "@/components/molecules/Tela.vue";

export default defineComponent({
  name: "Urna",
  components: { Teclado, Tela },
});
</script>

<style scoped>
.urna {
  width: 70%;
  height: 70vh;

  background-color: var(--ballot-box-background-color);
  padding: 30px;

  border-radius: 5px;

  display: flex;
}
</style>
