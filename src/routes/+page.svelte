
<h1>Welcome to SvelteKit</h1>
<p>Visit <a href="https://kit.svelte.dev">kit.svelte.dev</a> to read the documentation</p>
<h2>hello</h2>
<h2>POMOC!</h2>
<script>
    // Nastavení velikosti velkého obdélníku
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
    }
  </style>
  
  <div class="big-rectangle">
    <!-- Obsah velkého obdélníku bude sem -->
  </div>
  