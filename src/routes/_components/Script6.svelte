<script>
  let puppy = false

  function puppyButton() {
    puppy = !puppy
  }
</script>

<button on:click={puppyButton}>puppy button</button>

<div class="transition-bg" >
  {#if puppy}
    <img
      height="200"
      alt="A cute little pomeranian puppy"
      src="https://consumer-cms.petfinder.com/sites/default/files/images/content/Pomeranian%202.jpg"
    />
  {/if}
</div>

<style>
  .transition-bg {
    background-color: aliceblue;
  }
</style>
