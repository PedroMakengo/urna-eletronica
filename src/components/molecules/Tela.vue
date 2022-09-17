<template>
  <div class="urna-tela">
    <div v-if="tela != 'fim'" class="urna-tela-voto">
      <div class="urna-tela-voto-textos">
        <div class="urna-tela-voto-titulo">Seu voto para:</div>
        <div class="urna-tela-voto-tipo">{{ tela }}</div>

        <div class="urna-tela-voto-numeros">
          Números:
          <div
            v-for="(value, key) in numeroVoto.padEnd(quantidadeNumeros, ' ')"
            class="urna-tela-voto-numero"
            :key="key"
          >
            {{ value }}
          </div>
        </div>
      </div>
    </div>
    <div v-if="tela == 'fim'" class="urna-tela-fim">finalização</div>
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";

export default defineComponent({
  name: "Tela",
  props: {
    tela: String,
    numeroVoto: String,
    quantidadeNumeros: String,
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

.urna-tela-voto-titulo {
  font-size: 20px;
}

.urna-tela-voto-tipo {
  font-size: 30px;
  font-weight: bold;
  margin: 20px 0;
  text-transform: uppercase;
}
</style>
