<script>
  import Title from "./_components/Title.svelte"

  import Script1 from "./_components/Script1.svelte"
  import Script2 from "./_components/Script2.svelte"
  import Script3 from "./_components/Script3.svelte"
  import Script4 from "./_components/Script4.svelte"
  import Script5 from "./_components/Script5.svelte"
  import Script6 from "./_components/Script6.svelte"
  import Script7 from "./_components/Script7.svelte"
  import Script8 from "./_components/Script8.svelte"
</script>

<div class="container">
  <Title title="Svelte build system example" />

  <p>
    We're going to cover a few aspects of learning Svelte, but if you'd like to learn and practice in more detail, I
    highly recommend the official <a href="https://svelte.dev/tutorial/svelte/welcome-to-svelte">Svelte tutorial</a>!
  </p>

  <h3>Build system layout</h3>
  <p>Note that this HTML page is rendered in <span class="snippet">src/routes/index.svelte</span></p>

  <h3>D3 and Svelte</h3>

  <p>What's the difference between D3 and Svelte?</p>
  <p><strong>D3</strong> is a Javascript library:</p>
  <ul>
    <li>Collection of pre-written code that provides specific functions to make certain tasks easier</li>
    <li>
      Like <i>professional-grade equipment</i> in a kitchen -- tools made specially for blending, piping, slicing, etc --
      that reduces the required effort for specific tasks
    </li>
  </ul>
  <p><strong>Svelte</strong> is a Javascript-compiled framework:</p>
  <ul>
    <li>
      Takes high-level, highly-abstracted code (easier to read and comprehend by humans) and generates low-level, less
      abstracted code (easier for computers to parse). This makes code more lightweight and improves performance
    </li>
    <li>
      Like <i>the entire kitchen environment itself</i>, which affects workflow and overall experience. Svelte addresses
      issues of organization, ease of use, and seamless transition between different parts of the application in order
      to provide a better development experience for programmers.
    </li>
  </ul>
  <p>
    Another bonus of Svelte is that it works really well with D3. (<a href="https://www.youtube.com/watch?v=bnd64ZrHC0U"
      >This</a
    >
    a really good talk explaining more about why Svelte is great for D3 dataviz) <br />Svelte syntax slightly changes,
    since we write out the visualizations "literally" (more on that below) but the important thing to know is how to
    write SVGs -- which is what we've been doing!
  </p>

  <h2>Basic SVGs</h2>
  <p>
    In this exercise, we use the <span class="snippet">&lt;style&gt;</span> tags to set the colors of our SVGs. In
    Svelte, these styles are scoped to the component -- so these colors will only apply to the SVGs in
    <span class="snippet">Script1</span>!
  </p>
  <code>Script1.svelte</code>
  <Script1 />

  <h2>Looping through a dataset</h2>
  <code>Script2.svelte</code>
  <h3>&lbrace;#each&rbrace; and Svelte variables</h3>
  <p>
    #each blocks work like for loops in Python. These allow us to directly loop through the dataset while we write our
    SVGs and the other components of the chart.
  </p>
  <p>
    In Svelte, use curly braces (&lbrace; &rbrace;) to refer to variables or any Javascript you want. Any variables not
    placed in braces will be recognized as a string value.
  </p>

  <p>
    &lbrace;#each&rbrace;, like &lbrace;#if&rbrace;, requires closing blocks to complete the statement
    (&lbrace;/each&rbrace; or &lbrace;/if&rbrace;)
  </p>
  <Script2 />

  <h2>Importing D3</h2>
  <code>Script3.svelte</code>

  <p>
    Because we installed D3 with <span class="snippet">npm install d3</span>, we can call on it in our script:
    <span class="snippet"> import * as d3 from 'd3' </span>
  </p>
  <p>
    (You can also call D3 from your <span class="snippet">app.html</span> file by using the same code snippet as before)
  </p>

  <p>
    We also use <span class="snippet">onMount</span>, a Svelte function that tells D3 to refer to the Svelte document
    when looking for HTML elements.
  </p>

  <Script3 />

  <h2>Making a D3 chart</h2>
  <code>Script4.svelte</code>

  <p>
    We can use a dataset called <span class="snippet">dow_jones_2025.csv</span> thanks to configurations made in this build
    system that make it easy to parse and use CSVs.
  </p>

  <h3>Making visualizations "literally"</h3>

  <p>
    As we've seen, making graphics in D3 get a little clunky -- we have to use method chaining (<span class="snippet"
      >d3.method().anothermethod().yetanothermethod()</span
    >) to give instructions on how to make the graphic we have in mind.
  </p>

  <p>
    Svelte tries to simplify this by allowing a more "literal" way of writing graphics: adding each element, bit by bit,
    in the Svelte markup (which renders HTML by default, unless specified otherwise by <span class="snippet"
      >script</span
    >
    or <span class="snippet">style</span> tags) with the <span class="snippet">circle</span>,
    <span class="snippet">path</span>
    or <span class="snippet">rect</span> tags (to name a few) that we saw when we were first drawing SVGs.
  </p>

  <p>
    <a href="https://v4.connorrothschild.com/post/svelte-and-d3">Here's</a> a good write up explaining this concept in more
    detail.
  </p>

  <h3>Reactive statements</h3>
  <p>
    Another one of useful Svelte feature is the way it handles reactivity through the use of reactive statements (<span
      class="snippet">$:</span
    >)
  </p>

  <p>
    It signals to the computer that the <strong>variable is subject to change</strong> -- for example, new input data is
    added, or the browser size changes the necessary dimensions of the chart.
  </p>

  <h3>use:</h3>
  <p>
    The <span class="snippet">use:</span> tag in the HTML section of our Svelte markup is a way to call on functions we set
    in Javascript. In this example, we're calling on the D3 function that draws axes.
  </p>

  <h3>Dow Jones closing price in 2025</h3>
  <Script4 />
  <p class="data-source">
    Dow Jones data from <a href="https://www.wsj.com/market-data/quotes/index/DJIA/historical-prices"
      >Wall Street Journal</a
    >
  </p>

  <h2>Components and binding</h2>
  <code>Script5.svelte</code>

  <h3>Components</h3>

  <p>Components are self-contained and resuable Svelte scripts. They have a lot of advantages:</p>
  <ul>
    <li>They break up long scripts into smaller chunks of code, making projects easier to debug</li>
    <li>Components are reusable, so you can easily port them over within and across projects</li>
    <li>Because each component has its own script, you can define the behavior, structure, and appearance of each component independently</li>
  </ul>

  <p>Components can be audio components, axis components, tooltip components, map components, etc</p>

  <p>
    Import components in your <span class="snippet">&lt;script&gt;</span> tags, then call the component in the HTML section
    of your markup:
  </p>

  <span class="script-name">Script.Svelte</span>
  <div class="script">
    <pre>
    &lt;script&gt;
    import ComponentName from './Component.svelte'
&lt;/script&gt;

&lt;ComponentName /&gt;
  </pre>
  </div>

  <p>
    If your component <strong>requires an input</strong> in order to work, connect the two components with the same
    variable and an <span class="snippet">export let</span>:
  </p>

  <span class="script-name">main.Svelte</span>
  <div class="script">
    <pre>
      &lt;script&gt;
      import ComponentName from './Component.svelte'

      let variableName = "Mr. Smith"
&lt;/script&gt;
  
&lt;ComponentName &lbrace;variableName&rbrace; /&gt;
    </pre>
  </div>
  <span class="script-name">Component.Svelte</span>
  <div class="script">
    <pre>

&lt;script&gt;
    export let variableName
&lt;/script&gt;
     
    
&lt;p&gt;
    My dog's name is &lbrace;variableName&rbrace;
&lt;/p&gt;

&lt;ComponentName /&gt;
  </pre>
  </div>

  <h3>bind:</h3>

  <p>
    In Svelte, you can access and manipulate the dimensions/size of your chart elements dynamically, making it easy to
    create <strong>responsive charts</strong> (charts that adjust to the size of the browser)
  </p>

  <p>You can access the dimensions of HTML elements with these four Svelte values:</p>
  <ul>
    <li>
      <span class="snippet">clientWidth</span> and <span class="snippet">clientHeight</span>: retrieves dimensions of
      visible elements (excluding padding, border, etc)
    </li>
    <li>
      <span class="snippet">offsetWidth</span> and <span class="snippet">offsetHeight</span>: calculates entire width or
      height that HTML element takes up
    </li>
  </ul>

  <p>
    To create a two-way connection between the property or attribute of an HTML element with the variable in your
    component's JS code, you can use the Svelte notation <span class="snippet"><strong>bind:</strong></span>
  </p>

  <p>
    We also use the same <strong><span class="snippet">$:</span></strong> from above to indicate to the compiler which variables
    are subject to change.
  </p>

  <p>
    For example, if we wanted to create an SVG with a width responsive to the size of the browser, we could write
    something like:
  </p>

  
  <span class="script-name">chart.Svelte</span>
  <div class="script">
    <pre>
    &lt;script&gt;
      // svg dimensions
      let svg_width
      let svg_height = 500
      let margins = &lbrace;top:20, bottom:20, left:20, right:20&rbrace;
      $: chartWidth = svg_width - margins.left - margins.right
      let chartHeight = svg_height - margins.top - margins.bottom
  
      // scales
      $: xScale = d3.scaleLinear().domain([0, xMax]).range([0, chartWidth])
      let yScale = d3.scaleLinear().domain([0, yMax]).range([chartHeight, 0])
&lt;/script&gt;

&lt;div class="chart-space" <strong>bind:</strong>clientWidth=&lbrace;svg_width&rbrace;&gt;
  &lt;svg width=&lbrace;svg_width&rbrace; height=&lbrace;svg_height&rbrace;&gt;
    </pre>
  </div>
  <p>
    We use <span class="snippet">$:</span> for the variables <span class="snippet">chartWidth</span> and
    <span class="snippet">xScale</span>
    because they react to <span class="snippet">svg_width</span> and need to "listen" for changes.
  </p>

  <h3>on:</h3>
  <p>Event managing in Svelte is managed with <span class="snippet">on:</span>, and it works similarly to the way we learned this in D3:</p>

  <span class="snippet">on:eventName=&lbrace;functionName&rbrace;</span>

  <p>For example, if you wanted to console log the entry of every dot in a scatterplot, made from a dataset called <span class="snippet">dotData</span>:</p>
  <span class="script-name">example.Svelte</span>
  <div class="script">
    <pre>
      &lbrace;#each dotData as d&rbrace;
&lt;circle 
  cx=xScale(d.x) 
  cy=yScale(d.y)
  r=10
  <strong>on:mouseover</strong>=&lbrace;function() &lbrace; console.log(d) &rbrace;&rbrace
/&gt;
&lbrace;/each&rbrace;
    </pre>
  </div>

  <Script5 />

  <h2>Transitions</h2> <code>Script6.Svelte</code>
  <p>Transitions in Svelte operate the way we used them in D3: they require a <strong>start state</strong>, an <strong>end state</strong>, and they're responses to <strong>events</strong> (button clicks, scrolls, hovers, etc)</p>
  <p>You can set transitions in the CSS! The format is:</p>
  <pre>
    &lt;style&gt;
  selector &lbrace; 
    transition: property duration transition-type delay;
  &rbrace;
  &lt;/style&gt;
  </pre>
  <ul>
    <li>
      <strong>selector</strong>: HTML element(s) you want to apply transition to
    </li>
  <li><strong>property</strong>: property to be animated (background-color, width, height, etc)</li>
  <li><strong>duration</strong>: time it takes for animation to complete</li>
  <li><strong>transition-type</strong>: optional input that sets the transition type (linear, ease-in, ease-out, etc)</li>
  <li><strong>delay</strong>: optional input that specifies the length of delay before the transition starts</li>
</ul>

<p>Example events that you can listen for in the CSS include:</p>
<ul>
  <li><strong>hover</strong>: applies styles when element is being hovered over by the mouse</li>
  <li><strong>active</strong>: applies styles when element is being activated (e.g. mouse button held down)</li>
  <li><strong>focus</strong>: applies styles when element has focus (e.g. element clicked or tabbed into)</li>
  <li><strong>visited</strong>: applies styles to visited links</li>
</ul>
<p>We can change the color of the rectangle below by hovering over it...</p>
<svg width=200 height=50>
<rect  fill="skyblue"  x=50 y=0 width=50 height=50 />
</svg>
<p>... because we wrote the following in our style tag below:</p>
<pre>
  &lt;style&gt;
  rect &lbrace; 
    transition: fill 1s;
  &rbrace;
  rect:hover &lbrace; 
    fill:maroon;
  &rbrace;
&lt;/style&gt;
</pre>
<h3>Svelte transitions</h3>
<p>We can apply the same transition concepts in Svelte scripts!</p>
<p>There are seven transitions built into Svelte that can manipulate HTML elements in your script: <strong>fade, blur, fly, slide, scale, draw, crossfade</strong></p>

<p>Import them from the <span class="snippet">svelte/transition</span> module</p>

  <Script6/>



  <h2>Tweening</h2> <code>Script7.svelte</code> <code>Script8.svelte</code>
  <p>Svelte has ability to smoothly animate a value or set of values over time, in a process called <strong>tweening</strong>.</p>
  <p>You can choose the starting and ending values of a property, and Svelte will handle the rest by generating intermediate values to create the illusion of continuous motion.</p>
  <p>Import tweening capabilities via the <span class="snippet">svelte/motion</span> module:</p>
  <pre>
    &lt;script&gt;
    import &lbrace; tweened &rbrace; from 'svelte/motion'
&lt;/script&gt;
  </pre>

  <p>To set up tweened values:</p>
  <ol>
    <li>Import the tween module</li>
    <li>Set your initial values and the length of the animation</li>
    <span class="snippet">const tweenedValue = tweened(0, &lbrace;duration:1000&rbrace;)</span>
    <li>Set the final value</li>
    <span class="snippet">tweenedValue.set(100)</span>
  </ol>
  <p>Note: when you want to access the <span class="snippet">tweenedValue</span> in your HTML markup, remember to use <span class="snippet">$</span>, because it's a reactive variable!</p>
  <pre>
    &lt;p&gt; &lbrace; $tweenedValue &rbrace; &lt;/p&gt;
  </pre>

  <Script7 />

  <p>You can also tween arrays, i.e. turn one set of numbers into another!</p>

<p>This can become handy when you want to animate changing values in a chart. Here's a simple example, where we use two 1-dimensional arrays to change the x positions of circles in an SVG.</p>

<Script8 />
</div>

<style>
  .container {
    max-width: 700px;
    margin: 0 auto;
    /* padding: 0 2em; */
    padding-bottom: 2em;
  }

  #shapes {
    margin: 0 auto;
  }

  .chart-container {
    max-width: 500px;
    height: 200px;
    margin: 0 auto;
  }

  p {
    max-width: 700px;
  }

  rect {
    transition: fill 1s;
  }

  rect:hover {
    fill: maroon; 
  }
</style>
