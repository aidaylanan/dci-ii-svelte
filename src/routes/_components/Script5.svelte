<script>
  // In Script5.svelte, make a scatterplot:
  // 1. that uses data from flowerData.js (x: petal_length, y: sepal_length)
  // 2. that uses the XAxis, YAxis and Tooltip svelte components in this repo
  // 3. has a width that's responsive to browser size
  // 4. uses mouseover interactivity to activate the tooltip

  import flowerData from "../_data/flowerData.js"
  import XAxis from "./AxisX.svelte"
  import YAxis from "./AxisY.svelte"
  import Tooltip from "./Tooltip.svelte"
  import * as d3 from "d3"

  let margins = { top: 40, left: 20, bottom: 50, right: 40 }


  let petalLengths = flowerData.map(flowerData => flowerData.petal_length)
  let sepalLengths = flowerData.map(flowerData => flowerData.sepal_length)
  let xMax = d3.max(petalLengths)
  let yMax = d3.max(sepalLengths)

</script>


<style>
  .flower-dot:hover {
    cursor: pointer;
  }

  .chart-space {
    margin: 50px;
  }
</style>
