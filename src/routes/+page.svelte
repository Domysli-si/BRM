

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

