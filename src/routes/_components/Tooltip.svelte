<script>
	export let hoveredData;
</script>

<h1>Species: {hoveredData.species}</h1>
<h2><b>Sepal Length:</b> {hoveredData.sepal_length} | <b>Petal Length:</b> {hoveredData.petal_length}</h2>

 <style>
	 h1 {
    font-size: 1.5rem;
    font-weight: 500;
    margin-bottom: 5px;
    width: 100%;
	}

	h2 {
	    font-size: 0.8rem;
	    font-weight: 300;
	    text-transform: uppercase;
	}
 </style>