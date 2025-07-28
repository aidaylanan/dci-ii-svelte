<script>
  import { onMount } from "svelte"
  import * as d3 from "d3"

  onMount(async () => {
    // Make any D3 shape you'd like!
    let height = 300
    let width = 300

    let svg = d3.selectAll("#script-3")
    .append("svg")
    .attr("width", width)
    .attr("height", height)

    svg.append("rect")
    .attr("x", 100)
    .attr("y", 100)
    .attr("width", 20)
    .attr("height", 40)
    .attr("fill", "green")
  })
</script>

<div id="script-3" />
