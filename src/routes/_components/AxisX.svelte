<script>
    // Exporting xScale and height to make them accessible outside the component
    export let xScale;
    export let height;

    // Generate xTicks using the ticks() method of xScale with 6 ticks
    let xTicks = xScale.ticks(10);
</script>

<!-- Group element for x-axis ticks -->
<g class="xTicks" transform="translate(0, {height})">
    <!-- Iterate over xTicks using the each block -->
    {#each xTicks as tick}
        <!-- Create a group for each tick and transform it based on xScale value -->
        <g transform="translate({xScale(tick)}, 0)">
            <!-- Add the tick value as text -->
            <text x="0" y="0" dy="20" dominant-baseline="middle" text-anchor="middle">{tick}%</text>
            <!-- Draw a line representing the tick -->
            <line x1="0" y1="0" x2="0" y2="10" stroke="rgba(0, 0, 0, 0.25)" />
        </g>
    {/each}
</g>

<style>
    /* Styling for the text elements within the xTicks group */
    .xTicks text {
        font-size: 12px;
				fill: rgba(0, 0, 0, 0.25);
    }

	.xTicks line {
				fill: rgba(0, 0, 0, 0.25);
    }
		
</style>