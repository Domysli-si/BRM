<script>
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

  function getRandomInt(min, max) {
    min = Math.ceil(min);
    max = Math.floor(max);
    return Math.floor(Math.random() * (max - min + 1)) + min;
  }

  let books = []; // Seznam knih
  books.push({
    title: "Na západní frontě klid",
    author: "Erich Maria Remarque",
    genre: `román`,
    year: 1928,
    description:
      '<div style = "font-family: Arial Black;" class="my-class"> \
        <h1>Informace o knize</h1> \
        <li>Literární druh: epika </li> \
			<li>Literární směr: meziválečná próza </li> \
			<li>Časoprostor: 1. světová válka, hranice Francie a Německa </li> \
    </div>',
  });

  books.push({
    title: "Farma zvířat",
    author: "George Orwell",
    genre: `román`,
    year: 1945,
		description:
      '<div style = "font-family: Arial Black;" class="my-class"> \
        <h1>Informace o knize</h1> \
        <li>Literární druh: epika </li> \
			<li>Literární směr: meziválečná próza </li> \
			<li>Časoprostor: 1. světová válka, hranice Francie a Německa </li> \
    </div>',
  });

  books.push({
    title: "Proměna",
    author: "Franz Kafka",
    genre: `povídka`,
    year: 1915,
    description:
      '<div style = "font-family: Arial Black;" class="my-class"> \
        <h1>Informace o knize</h1> \
        <li>Literární druh: epika </li> \
			<li>Literární směr: meziválečná próza </li> \
			<li>Časoprostor: 1. světová válka, hranice Francie a Německa </li> \
    </div>',
  });

  // Nahraďte seznam knih v poli níže
  for (let i = 1; i <= 30; i++) {
    const random = getRandomInt(1, 6);
    let randomGenre = "";
    let randomAuthor = "";
    switch (random) {
      case 1:
        randomGenre = `elegie`;
        break;
      case 2:
        randomGenre = `román`;
        break;
      case 3:
        randomGenre = `povídka`;
        break;
      case 4:
        randomGenre = `legenda`;
        break;
      case 5:
        randomGenre = `komedie`;
        break;
      case 6:
        randomAuthor = `a`;
        break;
    }

    books.push({
      title: `Kniha ${i}`,
      author: randomAuthor,
      genre: randomGenre,
      year: 2020 + i,
    });
  }

  let selectedGenre = "";
  function filterByGenre(genre) {
    selectedGenre = genre;
  }

  let selectedAuthor = "";
  function filterByAuthor(author) {
    selectedAuthor = author;
  }
</script>

<style>
  body {
    background-color: #92ba92;
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
  }
  .header-container {
    background-color: #525e75;
    display: flex;
    justify-content: center;
    align-items: center;
    padding: 30px;
  }
  header {
    font-size: 2em;
    text-align: center;
    color: #f1ddbf;
    font-family: "Arial Black";
  }
  .book-container {
    display: flex;
    justify-content: flex-start; /* Zarovnání na levou stranu */
    align-items: left;
    flex-direction: column;
    padding: 20px;
    color: #f1ddbf;
    font-size: 18px;
    font-family: "Arial Black";
    text-align: center;
  }
  .book-list-container {
    max-width: calc(100%); /* Odstup od okraje */
    overflow-y: scroll;
    max-height: 60vh;
    padding-left: 20px; /* Odstup seznamu knih od levého okraje */
    overflow-x: hidden; /* Odebrání možnosti horizontálního posunu */
  }
  .book-list {
    width: 1000px;
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
    font-size: 3em; /* Velikost písma */
    font-family: "Arial Black";
    margin-top: 10px; /* Odsazení nadpisu od horního okraje */
    margin-left: 10px; /* Odsazení nadpisu od levého okraje */
    text-align: center;
    text-decoration-line: underline;
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
