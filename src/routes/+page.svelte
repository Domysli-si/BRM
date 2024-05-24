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

<script>
    let rectangles = ['A', 'B', 'C', 'D', 'E']; // Příklad dat, která budou zobrazena
    let currentIndex = 0;
  
    function prev() {
      currentIndex = currentIndex === 0 ? rectangles.length - 1 : currentIndex - 1;
    }
  
    function next() {
      currentIndex = currentIndex === rectangles.length - 1 ? 0 : currentIndex + 1;
    }
  
    const bigRectangleHeight = window.innerHeight / 3; // Třetina výšky okna
  </script>
  
  <style>
    /* Styly pro velký obdélník */
    .big-rectangle {
      width: 100%;
      height: {bigRectangleHeight}px;
      display: flex;
      justify-content: center;
      align-items: center;
      border: 2px solid black;
      overflow-x: auto; /* Povolit horizontální posouvání obsahu, pokud se nevejde */
      white-space: nowrap; /* Zamezí zalomení textu na více řádků */
    }
  
    /* Styly pro menší obdélníky */
    .small-rectangle {
      width: 100px;
      height: 50px;
      margin: 0 10px; /* Pro oddělení mezi obdélníky */
      background-color: lightblue;
      display: inline-block; /* Umožní menším obdélníkům být v jedné řadě */
    }
  </style>
  
  <div class="big-rectangle">
    {#each rectangles as rectangle}
      <div class="small-rectangle">{rectangle}</div>
    {/each}
  </div>
  
  <button on:click={prev}>Předchozí</button>
  <button on:click={next}>Další</button>
  