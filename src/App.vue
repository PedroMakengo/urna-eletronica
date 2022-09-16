<template>
  <div id="app">
    <Urna />
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";
import Urna from "@/components/Urna.vue";

export default defineComponent({
  components: { Urna },
});
</script>

<style scope>
#app {
  background-color: var(--background-color);
  width: 100%;
  height: 100%;

  display: flex;
  justify-content: center;
  align-items: center;
}
</style>
