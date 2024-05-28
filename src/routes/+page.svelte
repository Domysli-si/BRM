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

<style>

:global(body) {
  margin: 0;
  font-family: Arial, sans-serif;
  background: beige;
  height: 100vh;
}


  .header-container {
    background-color: rgba(188, 143, 143, 0.9); /* Průhledné pozadí */
    display: flex;
    justify-content: center;
    align-items: center;
    padding: 30px;
  }

  header {
    font-size: 2em;
    text-align: center;
    color: beige;
  }

  .book-container {
    display: flex;
    flex-direction: column;
    padding: 20px;
    color: black;
    text-align: left;
  }

  .book-list-container {
    overflow-y: auto;
    max-height: 60vh;
    padding-right: 20px; /* Přidání odsazení pro scrollbar */
    margin-right: 160px; /* Odstup od pravého okraje pro filtry */
    overflow-x: hidden; /* Odebrání možnosti horizontálního posunu */
  }

  .book-list {
    width: 100%; /* Šířka seznamu knih */
    padding: 10px; /* Odsazení obsahu seznamu knih */
  }

  .book {
    position: relative; /* Relativní pozice pro umístění textu */
    width: calc(100% - 20px); /* Zajištění správné šířky bez horizontálního scrollbaru */
    height: 200px;
    background-color: rgba(188, 143, 143, 0.9); /* Průhledné pozadí knih */
    margin-bottom: 10px;
    border-radius: 40px;
    box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
    display: flex;
    flex-direction: column; /* Umožňuje textu zaujímat horní roh */
    padding:10px;
  }

  .book-title {
    font-size: 2em; /* Velikost písma */
    font-family: 'Arial Black';
    color: black; /* Barva textu */
    margin-top: 10px; /* Odsazení nadpisu od horního okraje */
    text-align: center;
  }

  /* Styl pro kontejnery filtru */
  .filter-container {
    position: absolute;
    right: 20px;
    top: 325px;
    background-color: rgba(188, 143, 143, 0.9); /* Průhledné pozadí */
    padding: 10px;
    border-radius: 30px;
    display: flex;
    flex-direction: column;
    align-items: center;
  }

  .filter-button {
    width: 100px;
    height: 100px;
    margin: 5px;
    text-align: center;
    text-decoration: re;
    background-color: visible;
    border: none;
    cursor: pointer;
  }
</style>

<!-- Nadpis "Book Report Management" -->
<div class="header-container">
  <header>
    <h1>Book Report Management</h1> <!-- Zde je nadpis "Book Report Management" -->
  </header>
</div>

<!-- Filtry pro žánry -->
<div class="filter-container">
  <button class="filter-button" on:click={() => filterByGenre('')}>Zrušit filtr</button> <!-- Tlačítko pro zrušení filtru -->
  <button class="filter-button" on:click={() => filterByGenre('Žánr 1')}>Žánr 1</button> <!-- Tlačítko pro filtrování žánru 1 -->
  <button class="filter-button" on:click={() => filterByGenre('Žánr 2')}>Žánr 2</button> <!-- Tlačítko pro filtrování žánru 2 -->
  <button class="filter-button" on:click={() => filterByGenre('Žánr 3')}>Žánr 3</button> <!-- Tlačítko pro filtrování žánru 3 -->
  <button class="filter-button" on:click={() => filterByGenre('Žánr 4')}>Žánr 4</button> <!-- Tlačítko pro filtrování žánru 4 -->
  <button class="filter-button" on:click={() => filterByGenre('Žánr 5')}>Žánr 5</button> <!-- Tlačítko pro filtrování žánru 5 -->
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
