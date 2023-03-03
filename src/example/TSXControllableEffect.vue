<script lang="tsx">
import { defineComponent } from "vue";

interface PropsType {
  value: number;
}

const TSXControllableEffect = defineComponent<PropsType>((props, { emit }) => {
  return () => (
    <div>
      <p>TSX Controllable Effect</p>
      <p>{props.value}</p>
      <button
        onClick={() => {
          emit("update:value", props.value + 1);
        }}
      >
        value ++
      </button>
    </div>
  );
});

/**
 * 为什么需要这个❓
 * 因为TypeScript中定义的类型在运行时是不存在的。
 * vue不知道props类型的情况下, 会将外界传递的参数当作HTML属性。
 * 因此如果不写这句代码, 会导致无法获取到外界传递的参数。
 */

TSXControllableEffect.props = ["value"];

export default TSXControllableEffect;
</script>
