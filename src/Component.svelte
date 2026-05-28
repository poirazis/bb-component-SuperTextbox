<script>
  import { getContext } from "svelte";
  import { Textbox } from "@poirazis/supercomponents-shared";

  const { styleable } = getContext("sdk");
  const component = getContext("component");

  let {
    value = "",
    disabled = false,
    copyLabel = "Copy to clipboard",
    copiedLabel = "",
    wrap = false,
    monospace = true,
    onCopy,
  } = $props();

  function handleCopy(detail) {
    onCopy?.(detail);
  }
</script>

<div class="textbox-wrapper" use:styleable={$component.styles}>
  <Textbox
    {value}
    {disabled}
    {copyLabel}
    {copiedLabel}
    {wrap}
    {monospace}
    on:copy={handleCopy}
  />
</div>

<style>
  .textbox-wrapper {
    overflow: hidden;
  }
</style>
