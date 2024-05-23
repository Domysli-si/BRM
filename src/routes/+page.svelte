<h1>Welcome to SvelteKit</h1>
<p>Visit <a href="https://kit.svelte.dev">kit.svelte.dev</a> to read the documentation</p>
<h2>POMOC!</h2>
<script>
    import { onMount } from 'svelte';
  
    let canvas;
    let ctx;
  
    onMount(() => {
      ctx = canvas.getContext('2d');
      draw();
    });
  
    function draw() {
      if (!ctx) return;
      // Vymaž plátno
      ctx.clearRect(0, 0, canvas.width, canvas.height);
      // Nastav styl čáry
      ctx.strokeStyle = 'black';
      ctx.lineWidth = 2;
      // Nakresli čáru
      ctx.beginPath();
      ctx.moveTo(50, 50); // Počáteční bod (x, y)
      ctx.lineTo(200, 200); // Koncový bod (x, y)
      ctx.stroke();
    }
  </script>
  
  <style>
    canvas {
      border: 1px solid black;
    }
  </style>
  
  <canvas bind:this={canvas} width="400" height="400"></canvas>
  