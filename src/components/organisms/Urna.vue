<template>
  <div class="urna">
    <Tela
      :tela="tela"
      :numeroVoto="numeroVoto"
      :quantidadeNumeros="quantidadeNumeros"
      :candidato="candidato"
    />
    <Teclado
      :adicionarNumero="adicionarNumero"
      :corrigir="corrigir"
      :confirmar="confirmar"
      :votarEmBranco="votarEmBranco"
    />
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";
import Teclado from "@/components/molecules/Teclado.vue";
import Tela from "@/components/molecules/Tela.vue";

import confirmAudio from "@/assets/audios/confirm.wav";
import keyAudio from "@/assets/audios/key.wav";

export default defineComponent({
  name: "Urna",
  components: { Teclado, Tela },

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
      } as any,
    };
  },
  methods: {
    adicionarNumero(numero: number) {
      this.executarSom(keyAudio);
      // VERIFICA LIMITE DE NÚMEROS VOTADOS
      if (this.numeroVoto.length == this.quantidadeNumeros) {
        return false;
      }
      // ADICIONA O NÚMERO SELECIONADO
      this.numeroVoto += "" + numero;

      // VERIFICA CANDIDATO VOTADO
      this.verificarCandidato();
    },
    verificarCandidato() {
      if (this.numeroVoto.length < this.quantidadeNumeros) {
        return false;
      }

      // VERIFICA CANDIDATO EXISTENTE
      if (this.candidatos[this.tela][this.numeroVoto]) {
        this.candidato = this.candidatos[this.tela][this.numeroVoto];
        return true;
      }

      // VOTO NULO
      this.candidato = {
        name: "Voto nulo",
        partido: "Voto nulo",
        imagem: "",
      };
    },
    corrigir() {
      this.executarSom(keyAudio);
      this.limpar();
    },
    limpar() {
      this.candidato = {};
      this.numeroVoto = "";
    },
    confirmar() {
      if (this.numeroVoto.length < this.quantidadeNumeros) {
        return false;
      }
      return this.avancarTela();
    },
    avancarTela() {
      // CONFIRME SON
      this.executarSom(confirmAudio);

      if (this.tela == "prefeito") {
        this.tela = "vereador";
        this.quantidadeNumeros = 5;
        return this.limpar();
      }
      // FINALIZAÇÃO
      this.tela = "fim";

      // INSTANCIA ATUAL
      let instancia = this;

      setTimeout(function () {
        instancia.tela = "prefeito";
        instancia.quantidadeNumeros = 2;
        return instancia.limpar();
      }, 3000);
    },

    votarEmBranco() {
      if (this.tela == "fim") return false;

      this.limpar();
      this.avancarTela();
    },
    executarSom(arquivoSon: any) {
      if (arquivoSon) {
        let audio = new Audio(arquivoSon);
        audio.play();
      }
    },
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
