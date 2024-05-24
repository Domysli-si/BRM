<script>
  let rectangles = ["A", "B", "C", "D", "E"]; // Example data to be displayed
  let currentIndex = 0;

  function prev() {
    currentIndex =
      currentIndex === 0? rectangles.length - 1 : currentIndex - 1;
  }

  function next() {
    currentIndex =
      currentIndex === rectangles.length - 1? 0 : currentIndex + 1;
  }

  const bigRectangleHeight = window.innerHeight / 3; // One-third of the window height
</script>

<h1>Welcome to SvelteKit</h1>

<h1>Book Report Management</h1>

<h2>hello</h2>

<h2>POMOC!</h2>

<div class="big-rectangle">
  {#each rectangles as rectangle}
    <div class="small-rectangle">{rectangle}</div>
  {/each}
</div>

<button on:click={prev}>Previous</button>
<button on:click={next}>Next</button>

<style>
  /* Styles for the big rectangle */
 .big-rectangle {
    width: 100%;
    height: {bigRectangleHeight}px; /* Remove the curly braces around bigRectangleHeight */
    display: flex;
    justify-content: center;
    align-items: center;
    border: 2px solid black;
    overflow-x: auto; /* Enable horizontal scrolling if content doesn't fit */
    white-space: nowrap; /* Prevent text wrapping onto multiple lines */
  }

  /* Styles for the small rectangles */
 .small-rectangle {
    width: 100px;
    height: 50px;
    margin: 0 10px; /* Space between rectangles */
    background-color: lightblue;
    display: inline-block; /* Allow small rectangles to be in a single row */
  }
</style>