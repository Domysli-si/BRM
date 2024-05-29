<script>
  import BookDetails from "./BookDetails.svelte";

  let books = []; // Seznam knih
  books.push({
    title: "Na západní frontě klid",
    author: "Erich Maria Remarque",
    genre: "román",
    year: 1928,
    description: "Román o hrůzách první světové války.",
  });
  books.push({
    title: "Farma zvířat",
    author: "George Orwell",
    genre: "román",
    year: 1945,
    description: "Allegorický román kritizující totalitní režimy.",
  });
  books.push({
    title: "Proměna",
    author: "Franz Kafka",
    genre: "povídka",
    year: 1915,
    description: "Povídka o muži, který se promění v obřího brouka.",
  });

  function getRandomInt(min, max) {
    min = Math.ceil(min);
    max = Math.floor(max);
    return Math.floor(Math.random() * (max - min + 1)) + min;
  }

  for (let i = 1; i <= 30; i++) {
    const random = getRandomInt(1, 5);
    let randomGenre = "";
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
    }
    books.push({
      title: `Kniha ${i}`,
      author: `Autor ${i}`,
      genre: randomGenre,
      year: 2020 + i,
      description: `Popis knihy ${i}.`,
    });
  }

  let selectedGenre = "";

  function filterByGenre(genre) {
    selectedGenre = genre;
  }

  function openNewWindow(book) {
    const newWindow = window.open("", "_blank");
    newWindow.document.write(`
      <html>
        <head>
          <title>${book.title}</title>
          <style>
            body {
              background-color: #92ba92;
              font-family: "Arial Black";
              color: #f1ddbf;
            }
            .book-title {
              font-size: 2em;
              text-align: center;
              text-decoration: underline;
              margin-top: 20px;
            }
            .book-details {
              margin: 20px;
              font-size: 1.2em;
            }
          </style>
        </head>
        <body>
          <div class="book-title">${book.title}</div>
          <div class="book-details">
            <div>Autor: ${book.author}</div>
            <div>Rok vydání: ${book.year}</div>
            <div>Žánr: ${book.genre}</div>
            <div>Popis: ${book.description}</div>
          </div>
        </body>
      </html>
    `);
  }
</script>

<div class="header-container">
  <header>
    <h1>Book Report Management</h1>
  </header>
</div>

<div
  style="position: absolute;
         right: 200px; 
         top: 360px; 
         background-color:  #525e75; 
         padding: 10px; 
         border-radius: 30px;
         width: 300px;"
>
  <p>
    <button on:click={() => filterByGenre("")}>Zrušit filtr žánrů</button>
  </p>
  <p><button on:click={() => filterByGenre("román")}>Román</button></p>
  <p><button on:click={() => filterByGenre("elegie")}>Elegie</button></p>
  <p><button on:click={() => filterByGenre("povídka")}>Povídka</button></p>
  <p><button on:click={() => filterByGenre("legenda")}>Legenda</button></p>
  <p><button on:click={() => filterByGenre("komedie")}>Komedie</button></p>
</div>

<div class="book-container">
  <div class="book-list-container">
    <div class="book-list">
      {#each books as book}
        {#if !selectedGenre || book.genre === selectedGenre}
          <button
            class="book"
            on:click={() => openNewWindow(book)}
            on:keydown={(e) => {
              if (e.key === "Enter" || e.key === " ") openNewWindow(book);
            }}
          >
            <div class="book-title">{book.title}</div>
            <div>Autor: {book.author}</div>
            <div>Rok vydání: {book.year}</div>
            <div>Žánr: {book.genre}</div>
          </button>
        {/if}
      {/each}
    </div>
  </div>
</div>

<style>
  :global(body) {
    background-color: #92ba92;
  }
  button {
    text-align: right;
    font-family: "Arial Black";
    text-decoration: none;
    background-color: #78938a;
    border: none;
    cursor: pointer;
    border-radius: 5px;
    width: 300px;
    text-align: center;
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
    justify-content: flex-start;
    align-items: left;
    flex-direction: column;
    padding: 20px;
    color: #f1ddbf;
    font-size: 18px;
    font-family: "Arial Black";
    text-align: center;
  }

  .book-list-container {
    max-width: calc(100%);
    overflow-y: scroll;
    max-height: 60vh;
    padding-left: 20px;
    overflow-x: hidden;
  }

  .book-list {
    width: 500px;
    padding: 10px;
  }

  .book {
    position: relative;
    width: 100%;
    height: 200px;
    background-color: #525e75;
    margin-bottom: 10px;
    border-radius: 40px;
    box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
    display: flex;
    flex-direction: column;
    cursor: pointer;
  }

  .book-title {
    font-size: 2em;
    font-family: "Arial Black";
    margin-top: 10px;
    margin-left: 10px;
    text-align: center;
    text-decoration-line: underline;
    color: #f1ddbf;
  }
</style>
