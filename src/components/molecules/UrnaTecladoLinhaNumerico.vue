<template>
  <div class="urna-teclado-numerico-linha">
    <TeclaNumerico
      v-for="(num, index) of numsTeclado"
      :num="num"
      :key="index"
      @click="adicionarNumero(num)"
    />
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";
import TeclaNumerico from "@/components/atoms/TeclaNumerico.vue";

export default defineComponent({
  name: "UrnaTecladoLinhaNumerico",
  components: { TeclaNumerico },
  props: {
    numsTeclado: {
      type: String,
    },
    adicionarNumero: {
      type: Function,
    },
  },
});
</script>

<style scoped>
.urna-teclado-numerico-linha {
  display: flex;
  justify-content: space-around;
  margin-bottom: 20px;
}

.urna-teclado-numerico button {
  background-color: var(--ballot-box-keyboard-button-color);
  color: var(--light-text-color);
  font-size: 30px;
  border-radius: 5px;
  width: 80px;
  height: 50px;
}
</style>
