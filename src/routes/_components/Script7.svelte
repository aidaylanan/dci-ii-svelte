<script>
    import { tweened } from 'svelte/motion'

    let opacityValue = tweened(1, {duration:2000})
    let radiusValue = tweened(10, {duration:2000})

    function motion() {
        opacityValue.set(0)
        radiusValue.set(50)
    }
</script>

<p>Tweened opacity value: {$opacityValue}</p>
<button on:click={motion}>Grow and vanish</button>

<svg>
    <circle cx=100 cy=100 fill="pink" r={$radiusValue} opacity={$opacityValue}></circle>
</svg>