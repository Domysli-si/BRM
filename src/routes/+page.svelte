<script>
  let books = []; // Seznam knih

  // Nahraďte seznam knih v poli níže
  for (let i = 1; i <= 80; i++) {
    books.push({
      title: `Kniha ${i}`,
      author: `Autor ${i}`,
      genre: `Žánr ${i % 5}`, // Přidání informace o žánru
      year: 2020 + i // Přidání informace o roku vydání
    });
  }

  let selectedGenre = ''; // Uchovává vybraný žánr pro filtrování

  // Funkce pro filtrování podle žánru
  function filterByGenre(genre) {
    selectedGenre = genre; // Nastavení vybraného žánru pro filtrování
  }
</script>
<meta name="viewport" content="width=device-width, initial-scale=1.0">


<style>
  /* Stylizace zůstává stejná */
	button{
		text-align: right;
		font-family: 'Arial Black';
		text-decoration: none;
		background-color: beige;
		border: none;
		cursor: pointer;
		border-radius: 5px
		
		
	}
  .header-container {
    background-color: rosybrown;
    display: flex;
    justify-content: center;
    align-items: center;
    padding: 30px;
  }

  header {
    font-size: 2vw;
    text-align: center;
    color: beige;
  }

  .book-container {
    display: flex;
    justify-content: flex-start; /* Zarovnání na levou stranu */
    align-items: left;
    flex-direction: column;
		font-family: 'Arial Black';
    padding: 20px;
    color: black;
		
  }

  .book-list-container {
    max-width: calc(100%); /* Odstup od okraje */
    overflow-y: scroll;
    max-height: 60vh;
    padding-left: 20px; /* Odstup seznamu knih od levého okraje */
    overflow-x: hidden; /* Odebrání možnosti horizontálního posunu */
		position: sticky;
  }

  .book-list {
    width: 500px; /* Šířka seznamu knih */
    padding: 10px; /* Odsazení obsahu seznamu knih */
  }

  .book {
    position: relative; /* Relativní pozice pro umístění textu */
    width: 100%;
    height: 200px;
    background-color: rosybrown;
    margin-bottom: 10px;
    border-radius: 40px;
    box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
    display: flex;
    flex-direction: column; /* Umožňuje textu zaujímat horní roh */
  }

  .book-title {
    font-size: 2vw; /* Velikost písma */
		font-family: 'Arial Black';
    color: beige; /* Barva textu */
    margin-top: 10px; /* Odsazení nadpisu od horního okraje */
    margin-left: 10px; /* Odsazení nadpisu od levého okraje */
		text-align: center;
  }
</style>


<!-- Nadpis "Book Report Management" -->
<div class="header-container">
  <header>
    <h1>Book Report Management</h1> <!-- Zde je nadpis "Book Report Management" -->
  </header>
</div>

<!-- Filtry pro žánry -->

<div style="position: absolute; 
						right: 200px; 
						top: 360px; 
						background-color: rosybrown; 
						padding: 10px; 
						border-radius: 30px;
						width: 400px; 
           padding: 10px;
						
						">
	 <p> <button on:click={() => filterByGenre('')}>Zrušit filtr</button> </p> <!-- Tlačítko pro zrušení filtru -->
	<p>	<button on:click={() => filterByGenre('Žánr 1')}>Žánr 1</button> </p> <!-- Tlačítko pro filtrování žánru 1 -->
  <p> <button on:click={() => filterByGenre('Žánr 2')}>Žánr 2</button> </p> <!-- Tlačítko pro filtrování žánru 2 -->
  <p> <button on:click={() => filterByGenre('Žánr 3')}>Žánr 3</button> </p> <!-- Tlačítko pro filtrování žánru 3 -->
   <p><button on:click={() => filterByGenre('Žánr 4')}>Žánr 4</button> </p> <!-- Tlačítko pro filtrování žánru 4 -->
  <p> <button on:click={() => filterByGenre('Žánr 5')}>Žánr 5</button> </p> <!-- Tlačítko pro filtrování žánru 5 -->

	
 
</div>



<!-- Kontejner pro seznam knih -->
<div class="book-container">
  <h2 style="text-align: inherit;">Seznam knih</h2> <!-- Nadpis pro seznam knih, zarovnán na levou stranu -->
  <div class="book-list-container">
    <div class="book-list">
      {#each books as book}
        <!-- Přidání podmínky pro filtrování podle žánru -->
        {#if !selectedGenre || book.genre === selectedGenre}
          <div class="book">
            <div class="book-title">{book.title}</div> <!-- Zobrazení názvu knihy jako nadpis -->
            <div>Autor: {book.author}</div> <!-- Zobrazení autora -->
            <div>Rok vydání: {book.year}</div> <!-- Zobrazení roku vydání -->
            <div>Žánr: {book.genre}</div> <!-- Zobrazení žánru -->
          </div>
        {/if}
      {/each}
    </div>
  </div>
</div>
