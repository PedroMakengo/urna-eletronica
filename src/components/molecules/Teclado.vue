<template>
  <div class="urna-teclado">
    <div class="urna-teclado-numerico">
      <UrnaTecladoLinhaNumerico :numsTeclado="[1, 2, 3]" />
      <UrnaTecladoLinhaNumerico :numsTeclado="[4, 5, 6]" />
      <UrnaTecladoLinhaNumerico :numsTeclado="[7, 8, 9]" />
      <UrnaTecladoLinhaNumerico :numsTeclado="[0]" />
    </div>
    <div class="urna-teclado-acoes">
      <button class="btn-branco">BRANCO</button>
      <button class="btn-corrige">CORRIGE</button>
      <button class="btn-confirma">CONFIRMA</button>
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";
import UrnaTecladoLinhaNumerico from "@/components/molecules/UrnaTecladoLinhaNumerico.vue";

export default defineComponent({
  name: "Teclado",
  components: { UrnaTecladoLinhaNumerico },
});
</script>

<style scoped>
.urna-teclado {
  width: 40%;
  height: 100%;
  background-color: var(--ballot-box-keyboard-color);
  border-radius: 0.5rem;
  padding: 20px;

  display: flex;
  flex-direction: column;
  justify-content: center;
}

.urna-teclado-numerico {
  width: 100%;
}

.urna-teclado-acoes {
  width: 100%;
  display: flex;
  justify-content: space-around;
}

.urna-teclado-acoes button {
  color: var(--dark-text-color);
  font-size: 15px;
  border-radius: 5px;
  width: 30%;
  height: 50px;
}
.btn-branco {
  background-color: var(--ballot-box-white-button-color);
}
.btn-corrige {
  background-color: var(--ballot-box-correct-button-color);
}
.btn-confirma {
  background-color: var(--ballot-box-confirm-button-color);
}
</style>
