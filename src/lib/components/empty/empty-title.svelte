<script lang="ts">
  import { cn } from "$lib/utils.js";

  let {
    ref = $bindable(null),
    class: className,
    children,
    ...restProps
  } = $props();
</script>
<div
  bind:this={ref}
  data-slot="empty-title"
  class={cn("cn-font-heading text-base font-medium tracking-tight", className)}
  {...restProps}
>
  {@render children?.()}
</div>