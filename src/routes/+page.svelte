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
  .header-container {
    background-color: darkorange;
    display: flex;
    justify-content: center;
    align-items: center;
    padding: 30px;
  }

  header {
    font-size: 2em;
    text-align: center;
    color: black;
  }

  .book-container {
    display: flex;
    justify-content: flex-start; /* Zarovnání na levou stranu */
    align-items: center;
    flex-direction: column;
    padding: 20px;
    color: black;
  }

  .book-list-container {
    max-width: calc(100%); /* Odstup od okraje */
    overflow-y: auto;
    max-height: 60vh;
    padding-left: 20px; /* Odstup seznamu knih od levého okraje */
    overflow-x: hidden; /* Odebrání možnosti horizontálního posunu */
  }

  .book-list {
    width: 500px; /* Šířka seznamu knih */
    padding: 10px; /* Odsazení obsahu seznamu knih */
  }

  .book {
    position: relative; /* Relativní pozice pro umístění textu */
    width: 100%;
    height: 200px;
    background-color: darkorange;
    margin-bottom: 10px;
    border-radius: 40px;
    box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
    display: flex;
    flex-direction: column; /* Umožňuje textu zaujímat horní roh */
  }

  .book-title {
    font-size: 1em; /* Velikost písma */
    color: black; /* Barva textu */
    margin-top: 10px; /* Odsazení nadpisu od horního okraje */
    margin-left: 10px; /* Odsazení nadpisu od levého okraje */
  }
</style>


<!-- Nadpis "Book Report Management" -->
<div class="header-container">
  <header>
    <h1>Book Report Management</h1> <!-- Zde je nadpis "Book Report Management" -->
  </header>
</div>

<!-- Filtry pro žánry -->
<div style="position: absolute; right: 20px; top: 20px; background-color: darkorange; padding: 10px; border-radius: 5px;">
  <button on:click={() => filterByGenre('Žánr 1')}>Žánr 1</button> <!-- Tlačítko pro filtrování žánru 1 -->
  <button on:click={() => filterByGenre('Žánr 2')}>Žánr 2</button> <!-- Tlačítko pro filtrování žánru 2 -->
  <button on:click={() => filterByGenre('Žánr 3')}>Žánr 3</button> <!-- Tlačítko pro filtrování žánru 3 -->
  <button on:click={() => filterByGenre('Žánr 4')}>Žánr 4</button> <!-- Tlačítko pro filtrování žánru 4 -->
  <button on:click={() => filterByGenre('Žánr 5')}>Žánr 5</button> <!-- Tlačítko pro filtrování žánru 5 -->
  <button on:click={() => filterByGenre('')}>Zrušit filtr</button> <!-- Tlačítko pro zrušení filtru -->
</div>

<!-- Kontejner pro seznam knih -->
<div class="book-container">
  <h2 style="text-align: left;">Seznam knih</h2> <!-- Nadpis pro seznam knih, zarovnán na levou stranu -->
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
