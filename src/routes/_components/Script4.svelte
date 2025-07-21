<script>
  import data from "../_data/dow_jones_2025.csv"
  import * as d3 from "d3"

  let height = 400
  let width = 600

  let margin = { top: 10, bottom: 20, left: 40, right: 30 }

  let chartWidth = width - margin.left - margin.right
  let chartHeight = height - margin.top - margin.bottom

  const maxClose = d3.max(data, d => d.Close)

  // Reactive scales
  $: xScale = d3
    .scaleTime()
    .domain(d3.extent(data, d => d.Date))
    .range([0, chartWidth])
    

  $: yScale = d3.scaleLinear().domain([0, maxClose]).nice().range([chartHeight, 0])

  const parseDate = d3.timeParse("%m/%d/%y")

  data.forEach(function (d) {
    d.Date = parseDate(d.Date)
    d.Close = +d.Close
  })

  // console.log(data)

  $: line = d3
    .line()
    .x(function (d) {
      return xScale(d.Date)
    })
    .y(function (d) {
      return yScale(d.Close)
    })

  $: pathData = line(data)

  // Axis generators
  $: xAxis = d3.axisBottom(xScale)

  $: yAxis = d3.axisLeft(yScale)

  // Function to render axes 
  // We pass in the g element here
  function renderXAxis(node) {
    d3.select(node).call(xAxis)
  }

  function renderYAxis(node) {
    d3.select(node).call(yAxis)
  }
</script>

<div id="dow-jones">
  <svg {width} {height}>
    <g class="chart" transform="translate({margin.left}, {margin.top})">
      <path d={pathData} stroke="black" fill="none" />
      <g use:renderXAxis transform={`translate(0, ${chartHeight})`} />
      <g use:renderYAxis />
    </g>
  </svg>
</div>
