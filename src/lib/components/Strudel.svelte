<script lang="ts">
  let { tune } = $props();

let getStrudelURL = (tune: string) => {
  return "https://strudel.cc/#" + encodeURIComponent(btoa(tune))
}

</script>



<!-- svelte-ignore a11y_missing_attribute -->
<iframe src={getStrudelURL(tune)} width="100%" height="400px">
</iframe>