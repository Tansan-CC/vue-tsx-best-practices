<script lang="tsx">
interface PropsType {
  value?: number;
}

interface CtxType {
  emit: (event: string, ...args: any[]) => void;
}

export default (props: PropsType, ctx: CtxType) => {
  return (
    <div>
      <p>TSX Controllable</p>
      <p>{props.value}</p>
      <button
        onClick={() => {
          (props.value || props.value === 0) &&
            ctx.emit("update:value", props.value + 1);
        }}
      >
        value ++
      </button>
    </div>
  );
};
</script>
