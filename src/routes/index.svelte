<script>
  import Title from "./_components/Title.svelte"

  import Script1 from "./_components/Script1.svelte"
  import Script2 from "./_components/Script2.svelte"
  import Script3 from "./_components/Script3.svelte"
  import Script4 from "./_components/Script4.svelte"
  
</script>

<div class="container">
  <Title title="Svelte build system example" />

  <p>We're going to cover a few aspects of learning Svelte, but if you'd like to learn and practice in more detail, I highly recommend the official <a href="https://svelte.dev/tutorial/svelte/welcome-to-svelte">Svelte tutorial</a>!</p>

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
  <code>Script1.svelte</code>
  <Script1 />

  <h2>Looping through a dataset</h2>
  <code>Script2.svelte</code>
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
</style>
