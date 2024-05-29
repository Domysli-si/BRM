<script>
  // Funkce pro otevření nového okna s informacemi o knize
  function openNewWindow(book) {
    const newWindow = window.open("", "_blank");
    newWindow.document.write(`
      <html>
        <head>
          <title>${book.title}</title>
          <style>
            body { font-family: Arial Black; background-color: #92ba92; color: #f1ddbf; padding: 20px;}
            .book { background-color: #525e75; padding: 20px; border-radius: 10px; }
            .book-title { font-size: 2em; text-align: center; text-decoration-line: underline; }
          </style>
        </head>
        <body>
          <div class="book">
            <div class="book-title">${book.title}</div>
            <div>Autor: ${book.author}</div>
            <div>Rok vydání: ${book.year}</div>
            <div>Žánr: ${book.genre}</div>
            <div>${book.description}</div>
          </div>
        </body>
      </html>
    `);
  }

  // Funkce pro generování náhodného celého čísla v daném rozsahu
  function getRandomInt(min, max) {
    min = Math.ceil(min);
    max = Math.floor(max);
    return Math.floor(Math.random() * (max - min + 1)) + min;
  }

  // Seznam knih
  let books = [];

  // Přidání ručně zadaných knih
  books.push({
    title: "Na západní frontě klid",
    author: "Erich Maria Remarque",
    genre: "román",
    year: 1928,
    description:
      '<div class="my-class"> \
        <h1>Informace o knize</h1> \
        <li>Literární druh: epika </li> \
			<li>Literární směr: meziválečná próza </li> \
			<li>Časoprostor: 1. světová válka, hranice Francie a Německa </li> \
    </div>',
  });

  books.push({
    title: "Farma zvířat",
    author: "George Orwell",
    genre: "román",
    year: 1945,
		description:
      '<div style = "font-family: Arial Black;" class="my-class"> \
        <h1>Informace o knize</h1> \
        <li>Literární druh: epika </li> \
			<li>Literární směr: realismus, antiutopie </li> \
			<li>Časoprostor: 50. léta 20. století, v Anglii na venkově </li> \
    </div>',
  });

  books.push({
    title: "Proměna",
    author: "Franz Kafka",
    genre: "povídka",
    year: 1915,
    description:
      '<div style = "font-family: Arial Black;" class="my-class"> \
        <h1>Informace o knize</h1> \
        <li>Literární druh: epika </li> \
			<li>Literární směr: existencialismus </li> \
			<li>Časoprostor: čas není určen, maloměstský byt </li> \
    </div>',
  });

  // Generování dalších knih
  for (let i = 1; i <= 30; i++) {
    const random = getRandomInt(1, 6);
    let randomGenre = "";
    let randomAuthor = "";
    switch (random) {
      case 1:
        randomGenre = "elegie";
        break;
      case 2:
        randomGenre = "román";
        break;
      case 3:
        randomGenre = "povídka";
        break;
      case 4:
        randomGenre = "legenda";
        break;
      case 5:
        randomGenre = "komedie";
        break;
      case 6:
        randomAuthor = "a";
        break;
    }

    books.push({
      title: `Kniha ${i}`,
      author: randomAuthor,
      genre: randomGenre,
      year: 2020 + i,
    });
  }

  // Proměnné pro filtrování
  let selectedGenre = "";
  let selectedAuthor = "";

  // Funkce pro filtrování podle žánru
  function filterByGenre(genre) {
    selectedGenre = genre;
  }

  // Funkce pro filtrování podle autora
  function filterByAuthor(author) {
    selectedAuthor = author;
  }
</script>

<!-- Nadpis "Book Report Management" -->
<div class="header-container">
  <header>
    <h1>Book Report Management</h1>
  </header>
</div>

<!-- Filtry pro žánry -->
<body>
  <div
    style=" position: absolute;
						right: 200px; 
						top: 360px; 
						background-color:  black; 
						padding: 10px; 
						border-radius: 30px;
						width: 300px; 
           padding: 10px;"
  >
      <p>
        <button on:click={() => filterByGenre("")}>Zrušit filtr žánrů</button>
        <!-- Tlačítko pro zrušení filtru -->
      </p>
      <!--Genre-->
      <p><button on:click={() => filterByGenre("román")}>Román</button></p>
      <p><button on:click={() => filterByGenre("elegie")}>Elegie</button></p>
      <p><button on:click={() => filterByGenre("povídka")}>Povídka</button></p>
      <p><button on:click={() => filterByGenre("legenda")}>Legenda</button></p>
      <p><button on:click={() => filterByGenre("komedie")}>Komedie</button></p>

      <p><button on:click={() => filterByAuthor("a")}>a</button></p>
    </div>
    <!-- Kontejner pro seznam knih -->
    <div class="book-container">
      <div class="book-list-container">
        <div class="book-list">
          {#each books as book}
            <!-- Přidání podmínky pro filtrování podle žánru -->
            {#if !selectedGenre || book.genre === selectedGenre}
              <button
                class="book"
                on:click={() => openNewWindow(book)}
                on:keydown={(e) => {
                  if (e.key === "Enter" || e.key === " ") openNewWindow(book);
                }}
              >
                <div class="book-title">{book.title}</div>
                <!-- Zobrazení názvu knihy jako nadpis -->
                <div>Autor: {book.author}</div>
                <!-- Zobrazení autora -->
                <div>Rok vydání: {book.year}</div>
                <!-- Zobrazení roku vydání -->
                <div>Žánr: {book.genre}</div>
                <!-- Zobrazení žánru -->
              </button>
            {/if}
          {/each}
        </div>
      </div>
    </div>
  </body
>

<style>
  body {
    background-color: #92ba92; /* Pozadí stránky */
  }

  button {
    text-align: center;
    font-family: "Arial Black";
    text-decoration: none;
    background-color: #78938a;
    border: none;
    cursor: pointer;
    border-radius: 5px;
    width: 300px;
    color: #f1ddbf;
    margin-bottom: 5px;
  }

  .header-container {
    background-color: #525e75;
    display: flex;
    justify-content: center;
    align-items: center;
    padding: 30px;
  }

  header {
    font-size: 4em;
    text-align: center;
    color: #f1ddbf;
    font-family: "Arial Black";
  }

  /* Kontejner pro flexibilní rozložení */
  .container {
    display: flex;
    justify-content: space-between; /* Rozložení mezi dvěma částmi */
    align-items: flex-start; /* Zarovnání na horní okraj */
    padding: 20px;
  }

  /* Styly pro seznam knih */
  .book-container {
    flex: 1; /* Podíl na flexibilním prostoru pro zbytek */
    padding-right: 20px; /* Odstup od pravé strany */
  }

  /* Styly pro kontejner filtrů */
  .filter-container {
    width: 300px; /* Šířka kontejneru pro filtry */
  }

  .book-list-container {
    max-width: 100%; /* Odstup od okraje */
    overflow-y: scroll;
    max-height: 60vh;
    padding-left: 20px; /* Odstup seznamu knih od levého okraje */
    overflow-x: hidden; /* Odebrání možnosti horizontálního posunu */
  }

  .book-list {
    width: 100%; /* Zajistí, že seznam bude mít správnou šířku */
    padding: 10px;
  }

  .book {
    position: relative; /* Relativní pozice pro umístění textu */
    width: 100%;
    height: 200px;
    background-color: #525e75;
    margin-bottom: 10px;
    border-radius: 40px;
    box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
    display: flex;
    flex-direction: column; /* Umožňuje textu zaujímat horní roh */
    cursor: pointer; /* Změna kurzoru při najetí myší */
  }

  .book-title {
    font-size: 2em; /* Velikost písma */
    font-family: "Arial Black";
    margin-top: 10px; /* Odsazení nadpisu od horního okraje */
    margin-left: 10px; /* Odsazení nadpisu od levého okraje */
    text-align: center;
    text-decoration: underline;
    color: #f1ddbf;
  }
</style>

<!-- Nadpis "Book Report Management" -->
<div class="header-container">
  <header>
    <h1>Book Report Management</h1>
  </header>
</div>

<!-- Filtry pro žánry -->
<body>
  <div
    style=" position: absolute;
						right: 200px; 
						top: 360px; 
						background-color:   #525e75; 
						padding: 10px; 
						border-radius: 30px;
						width: 300px; 
           padding: 10px;"
  >
      <p>
        <button on:click={() => filterByGenre("")}>Zrušit filtr žánrů</button>
        <!-- Tlačítko pro zrušení filtru -->
      </p>
      <!--Genre-->
      <p><button on:click={() => filterByGenre("román")}>Román</button></p>
      <p><button on:click={() => filterByGenre("elegie")}>Elegie</button></p>
      <p><button on:click={() => filterByGenre("povídka")}>Povídka</button></p>
      <p><button on:click={() => filterByGenre("legenda")}>Legenda</button></p>
      <p><button on:click={() => filterByGenre("komedie")}>Komedie</button></p>

      <p><button on:click={() => filterByAuthor("a")}>a</button></p>
    </div>
    <!-- Kontejner pro seznam knih -->
    <div class="book-container">
      <div class="book-list-container">
        <div class="book-list">
          {#each books as book}
            <!-- Přidání podmínky pro filtrování podle žánru -->
            {#if !selectedGenre || book.genre === selectedGenre}
              <button
                class="book"
                on:click={() => openNewWindow(book)}
                on:keydown={(e) => {
                  if (e.key === "Enter" || e.key === " ") openNewWindow(book);
                }}
              >
                <div style = "font-family: Arial Black;"
									class="book-title">{book.title}</div>
                <!-- Zobrazení názvu knihy jako nadpis -->
                <div>Autor: {book.author}</div>
                <!-- Zobrazení autora -->
                <div>Rok vydání: {book.year}</div>
                <!-- Zobrazení roku vydání -->
                <div>Žánr: {book.genre}</div>
                <!-- Zobrazení žánru -->
              </button>
            {/if}
          {/each}
        </div>
      </div>
    </div>
  </body
>
