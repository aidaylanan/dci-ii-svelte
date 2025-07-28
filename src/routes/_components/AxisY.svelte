<script>
    export let yScale;
    export let width;

    let yTicks = yScale.ticks(4)
</script>

<g>
{#each yTicks as tick}
    <g transform="translate(0, {yScale(tick)})">
        <line x1={0} y1={0} x2={width} y2={0} stroke="#c4c4c4" stroke-width="0.5"/>
        <text x={0} y={-6}>{tick}</text>
    </g>
{/each}
</g>

<style>
    text {
        font-size: 12px;
				fill: rgba(0, 0, 0, 0.25);
    }
</style>