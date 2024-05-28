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
</script>

<style>
  :global(body) {
    margin: 0;
    font-family: Arial, sans-serif;
    background: beige;
    height: 100vh;
  }

  .header-container {
    background-color: rosybrown;
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
    justify-content: flex-start; /* Zarovnání na levou stranu */
    align-items: left;
    flex-direction: column;
    padding: 20px;
    color: black;
    text-align: left;
  }

  .book-list-container {
    max-width: calc(100%); /* Odstup od okraje */
    overflow-y: scroll;
    max-height: 60vh;
    padding-left: 20px; /* Odstup seznamu knih od levého okraje */
    overflow-x: hidden; /* Odebrání možnosti horizontálního posunu */
  }

  .book-list {
    width: 700px; /* Šířka seznamu knih */
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
    font-size: 2em; /* Velikost písma */
    font-family: 'Arial Black';
    color: black; /* Barva textu */
    margin-top: 10px; /* Odsazení nadpisu od horního okraje */
    margin-left: 10px; /* Odsazení nadpisu od levého okraje */
    text-align: center;
  }

  /* Responzivita */
  @media (max-width: 800px) {
    .book-list-container {
      padding-left: 0;
    }

    .book-list {
      width: 100%;
    }

    .book {
      border-radius: 20px;
      margin-left: 10px;
      margin-right: 10px;
    }
  }

  @media (max-width: 500px) {
    .book-title {
      font-size: 1.5em;
    }
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
            right: 50px; 
            top: 360px; 
            background-color: rosybrown; 
            padding: 10px; 
            border-radius: 30px;
            width: 400px; 
            padding: 10px;">
  <p> <button on:click={() => selectedGenre = ''}>Zrušit filtr</button> </p> <!-- Tlačítko pro zrušení filtru -->
  {#each Array.from({ length: 5 }, (_, i) => i + 1) as i}
    <p> <button on:click={() => selectedGenre = `Žánr ${i}`}>Žánr {i}</button> </p> <!-- Tlačítko pro filtrování žánru -->
  {/each}
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
