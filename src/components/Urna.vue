<template>
  <div class="urna">
    <Teclado />
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";
import Teclado from "@/components/Teclado.vue";

export default defineComponent({
  name: "Urna",
  components: { Teclado },
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
