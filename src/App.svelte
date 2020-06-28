<script lang="ts">
  import Sankey from "./Sankey.svelte";
  import graph from "./graph";

  let width = 500;
  let height = 500;

  let nodePadding = 0;
  let nodeAlign: "left" | "right" | "center" | "justify" | undefined = "left";
</script>

<style>
  .measure {
    position: absolute;
    top: 0;
    left: 0;
    width: 100vw;
    height: 100vh;
    pointer-events: none;
    /* background: rgba(255, 0, 0, 0.5); */
  }
</style>

<!-- <svelte:window bind:innerWidth={width} /> -->
<div class="measure" bind:offsetWidth={width} bind:offsetHeight={height} />

<select bind:value={nodeAlign}>
  <option value="left">Left</option>
  <option value="center">Center</option>
  <option value="right">Right</option>
  <option value="justify">Justify</option>
</select>

<input type="range" bind:value={nodePadding} min={0} max={20} step={1} />

<Sankey
  {graph}
  {width}
  {height}
  {nodePadding}
  {nodeAlign}
  extent={[[1, 1], [width - 1, height - 6]]} />
