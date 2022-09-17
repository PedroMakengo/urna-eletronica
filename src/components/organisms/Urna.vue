<template>
  <div class="urna">
    <Tela
      :tela="tela"
      :numeroVoto="numeroVoto"
      :quantidadeNumeros="quantidadeNumeros"
    />
    <Teclado :adicionarNumero="adicionarNumero" />
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";
import Teclado from "@/components/molecules/Teclado.vue";
import Tela from "@/components/molecules/Tela.vue";

export default defineComponent({
  name: "Urna",
  components: { Teclado, Tela },

  methods: {
    adicionarNumero(numero: any) {
      // VERIFICA LIMITE DE NÚMEROS VOTADOS
      if (this.numeroVoto.length == this.quantidadeNumeros) {
        return false;
      }
      // ADICIONA O NÚMERO SELECIONADO
      this.numeroVoto += "" + numero;
    },
  },

  data() {
    return {
      tela: "prefeito",
      numeroVoto: "",
      quantidadeNumeros: 2,
      candidato: {},
      candidatos: {
        prefeito: {
          "01": {
            nome: "Ash",
            partido: "Pokemon",
            imagem:
              "https://raw.githubusercontent.com/william-costa/wdev-urna-eletronica-resources/master/images/ash.png",
          },
          "08": {
            nome: "Vegeta",
            partido: "Dragon Ball",
            imagem:
              "https://raw.githubusercontent.com/william-costa/wdev-urna-eletronica-resources/master/images/vegeta.png",
          },
        },
        vereador: {
          "01234": {
            nome: "Pikachu",
            partido: "Pokemon",
            imagem:
              "https://raw.githubusercontent.com/william-costa/wdev-urna-eletronica-resources/master/images/pikachu.png",
          },
          "08001": {
            nome: "Goku",
            partido: "Dragon Ball",
            imagem:
              "https://raw.githubusercontent.com/william-costa/wdev-urna-eletronica-resources/master/images/goku.png",
          },
        },
      },
    };
  },
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
  justify-content: space-between;
}
</style>
