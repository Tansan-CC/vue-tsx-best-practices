<script lang="tsx">
import { defineComponent, ref } from "vue";

import TSX from "./example/TSX.vue";
import TSXControllable from "./example/TSXControllable.vue";
import TSXEffect from "./example/TSXEffect.vue";
import TSXControllableEffect from "./example/TSXControllableEffect.vue";
const value = ref(1);

export default defineComponent(() => {
  return () => (
    <>
      <TSX />
      <TSXEffect />
      <TSXControllable v-model:value={value.value} />
      <TSXControllableEffect v-model={[value.value, "value"]} />
    </>
  );
});
</script>

<!-- <template>
  <TSX />
  <TSXEffect />
  <TSXControllable v-model:value="value" />
  <TSXControllableEffect v-model:value="value" />
</template> -->

<style scoped>
div {
  margin: 20px;
  padding: 10px;
  background-color: black;
  color: white;
  font-weight: bold;
}

div :deep(p) {
  color: white;
  font-weight: bold;
}
</style>
