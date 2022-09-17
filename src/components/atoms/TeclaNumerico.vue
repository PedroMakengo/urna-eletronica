<template>
  <button type="button">{{ num }}</button>
</template>

<script lang="ts">
import { defineComponent } from "vue";

export default defineComponent({
  name: "TeclaNumerico",
  props: { num: { type: String } },
});
</script>

<style scoped></style>
