<script>
    import { tweened } from 'svelte/motion'

    // our x values for the circles
    let dataA = [40, 120,  87, 159, 168]
    let dataB = [80, 150, 78, 297, 69]

    // initiate a tweened variable
    // const tweenedValue = 

    // function call for first button
    function callA() {
        // 
    }

    // function call for second button
    function callB() {
        // 
    }
</script>

<p>
    <svg height=200 width=400>
        <!-- iterate through every value in the array -->
        
        <!-- set the x value of each circle according to the current tweened value -->
        <circle cx={value} cy=100 r=15 opacity=0.5 fill="skyblue"></circle>
        
    </svg>
</p>

<button on:click={callA}>Dataset A</button>
<button on:click={callB}>Dataset B</button>