<template>
  <div class="urna-teclado">
    <div class="urna-teclado-numerico">
      <UrnaTecladoLinhaNumerico
        :numsTeclado="[1, 2, 3]"
        :adicionarNumero="adicionarNumero"
      />
      <UrnaTecladoLinhaNumerico
        :numsTeclado="[4, 5, 6]"
        :adicionarNumero="adicionarNumero"
      />
      <UrnaTecladoLinhaNumerico
        :numsTeclado="[7, 8, 9]"
        :adicionarNumero="adicionarNumero"
      />
      <UrnaTecladoLinhaNumerico
        :numsTeclado="[0]"
        :adicionarNumero="adicionarNumero"
      />
    </div>
    <div class="urna-teclado-acoes">
      <button type="button" @click="votarEmBranco()" class="btn-branco">
        BRANCO
      </button>
      <button type="button" @click="corrigir()" class="btn-corrige">
        CORRIGE
      </button>
      <button type="button" @click="confirmar()" class="btn-confirma">
        CONFIRMA
      </button>
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";
import UrnaTecladoLinhaNumerico from "@/components/molecules/UrnaTecladoLinhaNumerico.vue";

export default defineComponent({
  name: "Teclado",
  components: { UrnaTecladoLinhaNumerico },
  props: {
    adicionarNumero: Function,
    corrigir: Function,
    confirmar: Function,
    votarEmBranco: Function,
  },
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
