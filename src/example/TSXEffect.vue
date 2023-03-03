<script lang="tsx">
import { defineComponent, ref } from "vue";

/**
 * 需要注意, 这里不能用函数定义。
 * 因为函数定义的组件, 在vue监测到内部响应式数据变化时, 会重新执行函数。
 * 此时响应式数据会被重新定义, 从而导致组件无法响应式更新。
 */
export default defineComponent(() => {
  const value = ref(0);
  // 返回的是一个函数❕
  return () => (
    <div>
      <p>TSX Effect</p>
      <p>{value.value}</p>
      <button
        onClick={() => {
          value.value++;
        }}
      >
        value ++
      </button>
    </div>
  );
});
</script>
