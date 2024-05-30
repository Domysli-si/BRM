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
            .book-title { font-size: 2em; text-align: center; }
          </style>
					
        </head>
        <body>
          <div class="book">
            <div style="font-family: Arial Black;" class="book-title">${book.title}</div>
						<div style = 
						"text-align:right;
						 top: 1000px;"> 
						<a href="#section-1">Informace o knize</a><br />
            <a href="#section-2">Informace o autorovi</a><br />
            <a href="#section-3">Shrnutí</a><br />
						</div>
						
            <div>Autor: ${book.author}</div>
            <div>Rok vydání: ${book.year}</div>
            <div>Žánr: ${book.genre}</div>

            <div>
						<h1 id = "section-1">Informace o knize</h1>
						<p>${book.book_description}</p>
						</div>
						<div>
						<h1 id = "section-2">Informace o autorovi</h1></div>
						<p>${book.author_description}</p>
						<div>
						<h1 id = "section-3">Shrnutí</h1>
						<p>${book.summary}</p>
						</div>
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
     book_description:
      '<div style = "font-family: Arial Black;" class="my-class"> \
        <li>Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Sit amet porttitor eget dolor morbi non. Posuere sollicitudin aliquam ultrices sagittis orci a scelerisque. Euismod nisi porta lorem mollis aliquam ut porttitor leo. Enim nulla aliquet porttitor lacus. Praesent tristique magna sit amet. Nibh venenatis cras sed felis eget velit aliquet. Facilisis leo vel fringilla est ullamcorper. Feugiat nisl pretium fusce id. Elementum nibh tellus molestie nunc non. Semper eget duis at tellus at urna condimentum. Semper quis lectus nulla at volutpat. Duis convallis convallis tellus id interdum velit laoreet id donec. Integer eget aliquet nibh praesent tristique magna sit. Pharetra pharetra massa massa ultricies. Suspendisse interdum consectetur libero id faucibus nisl tincidunt eget. Dictum varius duis at consectetur. Sed ullamcorper morbi tincidunt ornare massa eget egestas purus. </li> \
			<li>Et malesuada fames ac turpis. Maecenas volutpat blandit aliquam etiam. Leo in vitae turpis massa. Massa eget egestas purus viverra accumsan in. Volutpat est velit egestas dui id ornare. Felis bibendum ut tristique et. Non quam lacus suspendisse faucibus interdum posuere. Dictum at tempor commodo ullamcorper a lacus. Augue neque gravida in fermentum. Elementum integer enim neque volutpat ac tincidunt. Scelerisque purus semper eget duis at. </li> \
			<li>Arcu bibendum at varius vel pharetra vel turpis. Turpis egestas pretium aenean pharetra magna ac. Ultricies mi quis hendrerit dolor. Eu facilisis sed odio morbi quis. Tempor commodo ullamcorper a lacus vestibulum sed arcu non odio. Adipiscing commodo elit at imperdiet dui accumsan sit amet nulla. In est ante in nibh mauris cursus mattis. Nunc sed velit dignissim sodales ut eu sem. Volutpat diam ut venenatis tellus in metus vulputate. Aliquet nibh praesent tristique magna. Urna neque viverra justo nec. Scelerisque eu ultrices vitae auctor eu augue ut lectus. </li> \
    </div>',
		author_description:  '<div style = "font-family: Arial Black;" class="my-class"> \
        <li>Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Sit amet porttitor eget dolor morbi non. Posuere sollicitudin aliquam ultrices sagittis orci a scelerisque. Euismod nisi porta lorem mollis aliquam ut porttitor leo. Enim nulla aliquet porttitor lacus. Praesent tristique magna sit amet. Nibh venenatis cras sed felis eget velit aliquet. Facilisis leo vel fringilla est ullamcorper. Feugiat nisl pretium fusce id. Elementum nibh tellus molestie nunc non. Semper eget duis at tellus at urna condimentum. Semper quis lectus nulla at volutpat. Duis convallis convallis tellus id interdum velit laoreet id donec. Integer eget aliquet nibh praesent tristique magna sit. Pharetra pharetra massa massa ultricies. Suspendisse interdum consectetur libero id faucibus nisl tincidunt eget. Dictum varius duis at consectetur. Sed ullamcorper morbi tincidunt ornare massa eget egestas purus. </li> \
			<li>Et malesuada fames ac turpis. Maecenas volutpat blandit aliquam etiam. Leo in vitae turpis massa. Massa eget egestas purus viverra accumsan in. Volutpat est velit egestas dui id ornare. Felis bibendum ut tristique et. Non quam lacus suspendisse faucibus interdum posuere. Dictum at tempor commodo ullamcorper a lacus. Augue neque gravida in fermentum. Elementum integer enim neque volutpat ac tincidunt. Scelerisque purus semper eget duis at. </li> \
			<li>Arcu bibendum at varius vel pharetra vel turpis. Turpis egestas pretium aenean pharetra magna ac. Ultricies mi quis hendrerit dolor. Eu facilisis sed odio morbi quis. Tempor commodo ullamcorper a lacus vestibulum sed arcu non odio. Adipiscing commodo elit at imperdiet dui accumsan sit amet nulla. In est ante in nibh mauris cursus mattis. Nunc sed velit dignissim sodales ut eu sem. Volutpat diam ut venenatis tellus in metus vulputate. Aliquet nibh praesent tristique magna. Urna neque viverra justo nec. Scelerisque eu ultrices vitae auctor eu augue ut lectus. </li> \
    </div>',
		summary:  '<div style = "font-family: Arial Black;" class="my-class"> \
        <li>Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Sit amet porttitor eget dolor morbi non. Posuere sollicitudin aliquam ultrices sagittis orci a scelerisque. Euismod nisi porta lorem mollis aliquam ut porttitor leo. Enim nulla aliquet porttitor lacus. Praesent tristique magna sit amet. Nibh venenatis cras sed felis eget velit aliquet. Facilisis leo vel fringilla est ullamcorper. Feugiat nisl pretium fusce id. Elementum nibh tellus molestie nunc non. Semper eget duis at tellus at urna condimentum. Semper quis lectus nulla at volutpat. Duis convallis convallis tellus id interdum velit laoreet id donec. Integer eget aliquet nibh praesent tristique magna sit. Pharetra pharetra massa massa ultricies. Suspendisse interdum consectetur libero id faucibus nisl tincidunt eget. Dictum varius duis at consectetur. Sed ullamcorper morbi tincidunt ornare massa eget egestas purus. </li> \
			<li>Et malesuada fames ac turpis. Maecenas volutpat blandit aliquam etiam. Leo in vitae turpis massa. Massa eget egestas purus viverra accumsan in. Volutpat est velit egestas dui id ornare. Felis bibendum ut tristique et. Non quam lacus suspendisse faucibus interdum posuere. Dictum at tempor commodo ullamcorper a lacus. Augue neque gravida in fermentum. Elementum integer enim neque volutpat ac tincidunt. Scelerisque purus semper eget duis at. </li> \
			<li>Arcu bibendum at varius vel pharetra vel turpis. Turpis egestas pretium aenean pharetra magna ac. Ultricies mi quis hendrerit dolor. Eu facilisis sed odio morbi quis. Tempor commodo ullamcorper a lacus vestibulum sed arcu non odio. Adipiscing commodo elit at imperdiet dui accumsan sit amet nulla. In est ante in nibh mauris cursus mattis. Nunc sed velit dignissim sodales ut eu sem. Volutpat diam ut venenatis tellus in metus vulputate. Aliquet nibh praesent tristique magna. Urna neque viverra justo nec. Scelerisque eu ultrices vitae auctor eu augue ut lectus. </li> \
    </div>',
  });

  books.push({
    title: "Farma zvířat",
    author: "George Orwell",
    genre: "román",
    year: 1945,
		 book_description:
      '<div style = "font-family: Arial Black;" class="my-class"> \
        <li>Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Sit amet porttitor eget dolor morbi non. Posuere sollicitudin aliquam ultrices sagittis orci a scelerisque. Euismod nisi porta lorem mollis aliquam ut porttitor leo. Enim nulla aliquet porttitor lacus. Praesent tristique magna sit amet. Nibh venenatis cras sed felis eget velit aliquet. Facilisis leo vel fringilla est ullamcorper. Feugiat nisl pretium fusce id. Elementum nibh tellus molestie nunc non. Semper eget duis at tellus at urna condimentum. Semper quis lectus nulla at volutpat. Duis convallis convallis tellus id interdum velit laoreet id donec. Integer eget aliquet nibh praesent tristique magna sit. Pharetra pharetra massa massa ultricies. Suspendisse interdum consectetur libero id faucibus nisl tincidunt eget. Dictum varius duis at consectetur. Sed ullamcorper morbi tincidunt ornare massa eget egestas purus. </li> \
			<li>Et malesuada fames ac turpis. Maecenas volutpat blandit aliquam etiam. Leo in vitae turpis massa. Massa eget egestas purus viverra accumsan in. Volutpat est velit egestas dui id ornare. Felis bibendum ut tristique et. Non quam lacus suspendisse faucibus interdum posuere. Dictum at tempor commodo ullamcorper a lacus. Augue neque gravida in fermentum. Elementum integer enim neque volutpat ac tincidunt. Scelerisque purus semper eget duis at. </li> \
			<li>Arcu bibendum at varius vel pharetra vel turpis. Turpis egestas pretium aenean pharetra magna ac. Ultricies mi quis hendrerit dolor. Eu facilisis sed odio morbi quis. Tempor commodo ullamcorper a lacus vestibulum sed arcu non odio. Adipiscing commodo elit at imperdiet dui accumsan sit amet nulla. In est ante in nibh mauris cursus mattis. Nunc sed velit dignissim sodales ut eu sem. Volutpat diam ut venenatis tellus in metus vulputate. Aliquet nibh praesent tristique magna. Urna neque viverra justo nec. Scelerisque eu ultrices vitae auctor eu augue ut lectus. </li> \
    </div>',
		author_description:  '<div style = "font-family: Arial Black;" class="my-class"> \
        <li>Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Sit amet porttitor eget dolor morbi non. Posuere sollicitudin aliquam ultrices sagittis orci a scelerisque. Euismod nisi porta lorem mollis aliquam ut porttitor leo. Enim nulla aliquet porttitor lacus. Praesent tristique magna sit amet. Nibh venenatis cras sed felis eget velit aliquet. Facilisis leo vel fringilla est ullamcorper. Feugiat nisl pretium fusce id. Elementum nibh tellus molestie nunc non. Semper eget duis at tellus at urna condimentum. Semper quis lectus nulla at volutpat. Duis convallis convallis tellus id interdum velit laoreet id donec. Integer eget aliquet nibh praesent tristique magna sit. Pharetra pharetra massa massa ultricies. Suspendisse interdum consectetur libero id faucibus nisl tincidunt eget. Dictum varius duis at consectetur. Sed ullamcorper morbi tincidunt ornare massa eget egestas purus. </li> \
			<li>Et malesuada fames ac turpis. Maecenas volutpat blandit aliquam etiam. Leo in vitae turpis massa. Massa eget egestas purus viverra accumsan in. Volutpat est velit egestas dui id ornare. Felis bibendum ut tristique et. Non quam lacus suspendisse faucibus interdum posuere. Dictum at tempor commodo ullamcorper a lacus. Augue neque gravida in fermentum. Elementum integer enim neque volutpat ac tincidunt. Scelerisque purus semper eget duis at. </li> \
			<li>Arcu bibendum at varius vel pharetra vel turpis. Turpis egestas pretium aenean pharetra magna ac. Ultricies mi quis hendrerit dolor. Eu facilisis sed odio morbi quis. Tempor commodo ullamcorper a lacus vestibulum sed arcu non odio. Adipiscing commodo elit at imperdiet dui accumsan sit amet nulla. In est ante in nibh mauris cursus mattis. Nunc sed velit dignissim sodales ut eu sem. Volutpat diam ut venenatis tellus in metus vulputate. Aliquet nibh praesent tristique magna. Urna neque viverra justo nec. Scelerisque eu ultrices vitae auctor eu augue ut lectus. </li> \
    </div>',
		summary:  '<div style = "font-family: Arial Black;" class="my-class"> \
        <li>Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Sit amet porttitor eget dolor morbi non. Posuere sollicitudin aliquam ultrices sagittis orci a scelerisque. Euismod nisi porta lorem mollis aliquam ut porttitor leo. Enim nulla aliquet porttitor lacus. Praesent tristique magna sit amet. Nibh venenatis cras sed felis eget velit aliquet. Facilisis leo vel fringilla est ullamcorper. Feugiat nisl pretium fusce id. Elementum nibh tellus molestie nunc non. Semper eget duis at tellus at urna condimentum. Semper quis lectus nulla at volutpat. Duis convallis convallis tellus id interdum velit laoreet id donec. Integer eget aliquet nibh praesent tristique magna sit. Pharetra pharetra massa massa ultricies. Suspendisse interdum consectetur libero id faucibus nisl tincidunt eget. Dictum varius duis at consectetur. Sed ullamcorper morbi tincidunt ornare massa eget egestas purus. </li> \
			<li>Et malesuada fames ac turpis. Maecenas volutpat blandit aliquam etiam. Leo in vitae turpis massa. Massa eget egestas purus viverra accumsan in. Volutpat est velit egestas dui id ornare. Felis bibendum ut tristique et. Non quam lacus suspendisse faucibus interdum posuere. Dictum at tempor commodo ullamcorper a lacus. Augue neque gravida in fermentum. Elementum integer enim neque volutpat ac tincidunt. Scelerisque purus semper eget duis at. </li> \
			<li>Arcu bibendum at varius vel pharetra vel turpis. Turpis egestas pretium aenean pharetra magna ac. Ultricies mi quis hendrerit dolor. Eu facilisis sed odio morbi quis. Tempor commodo ullamcorper a lacus vestibulum sed arcu non odio. Adipiscing commodo elit at imperdiet dui accumsan sit amet nulla. In est ante in nibh mauris cursus mattis. Nunc sed velit dignissim sodales ut eu sem. Volutpat diam ut venenatis tellus in metus vulputate. Aliquet nibh praesent tristique magna. Urna neque viverra justo nec. Scelerisque eu ultrices vitae auctor eu augue ut lectus. </li> \
    </div>',
  });

  books.push({
    title: "Proměna",
    author: "Franz Kafka",
    genre: "povídka",
    year: 1915,
    description: "Povídka o muži, který se promění v obřího brouka.",
		 book_description:
      '<div style = "font-family: Arial Black;" class="my-class"> \
        <li>Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Sit amet porttitor eget dolor morbi non. Posuere sollicitudin aliquam ultrices sagittis orci a scelerisque. Euismod nisi porta lorem mollis aliquam ut porttitor leo. Enim nulla aliquet porttitor lacus. Praesent tristique magna sit amet. Nibh venenatis cras sed felis eget velit aliquet. Facilisis leo vel fringilla est ullamcorper. Feugiat nisl pretium fusce id. Elementum nibh tellus molestie nunc non. Semper eget duis at tellus at urna condimentum. Semper quis lectus nulla at volutpat. Duis convallis convallis tellus id interdum velit laoreet id donec. Integer eget aliquet nibh praesent tristique magna sit. Pharetra pharetra massa massa ultricies. Suspendisse interdum consectetur libero id faucibus nisl tincidunt eget. Dictum varius duis at consectetur. Sed ullamcorper morbi tincidunt ornare massa eget egestas purus. </li> \
			<li>Et malesuada fames ac turpis. Maecenas volutpat blandit aliquam etiam. Leo in vitae turpis massa. Massa eget egestas purus viverra accumsan in. Volutpat est velit egestas dui id ornare. Felis bibendum ut tristique et. Non quam lacus suspendisse faucibus interdum posuere. Dictum at tempor commodo ullamcorper a lacus. Augue neque gravida in fermentum. Elementum integer enim neque volutpat ac tincidunt. Scelerisque purus semper eget duis at. </li> \
			<li>Arcu bibendum at varius vel pharetra vel turpis. Turpis egestas pretium aenean pharetra magna ac. Ultricies mi quis hendrerit dolor. Eu facilisis sed odio morbi quis. Tempor commodo ullamcorper a lacus vestibulum sed arcu non odio. Adipiscing commodo elit at imperdiet dui accumsan sit amet nulla. In est ante in nibh mauris cursus mattis. Nunc sed velit dignissim sodales ut eu sem. Volutpat diam ut venenatis tellus in metus vulputate. Aliquet nibh praesent tristique magna. Urna neque viverra justo nec. Scelerisque eu ultrices vitae auctor eu augue ut lectus. </li> \
    </div>',
		author_description:  '<div style = "font-family: Arial Black;" class="my-class"> \
        <li>Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Sit amet porttitor eget dolor morbi non. Posuere sollicitudin aliquam ultrices sagittis orci a scelerisque. Euismod nisi porta lorem mollis aliquam ut porttitor leo. Enim nulla aliquet porttitor lacus. Praesent tristique magna sit amet. Nibh venenatis cras sed felis eget velit aliquet. Facilisis leo vel fringilla est ullamcorper. Feugiat nisl pretium fusce id. Elementum nibh tellus molestie nunc non. Semper eget duis at tellus at urna condimentum. Semper quis lectus nulla at volutpat. Duis convallis convallis tellus id interdum velit laoreet id donec. Integer eget aliquet nibh praesent tristique magna sit. Pharetra pharetra massa massa ultricies. Suspendisse interdum consectetur libero id faucibus nisl tincidunt eget. Dictum varius duis at consectetur. Sed ullamcorper morbi tincidunt ornare massa eget egestas purus. </li> \
			<li>Et malesuada fames ac turpis. Maecenas volutpat blandit aliquam etiam. Leo in vitae turpis massa. Massa eget egestas purus viverra accumsan in. Volutpat est velit egestas dui id ornare. Felis bibendum ut tristique et. Non quam lacus suspendisse faucibus interdum posuere. Dictum at tempor commodo ullamcorper a lacus. Augue neque gravida in fermentum. Elementum integer enim neque volutpat ac tincidunt. Scelerisque purus semper eget duis at. </li> \
			<li>Arcu bibendum at varius vel pharetra vel turpis. Turpis egestas pretium aenean pharetra magna ac. Ultricies mi quis hendrerit dolor. Eu facilisis sed odio morbi quis. Tempor commodo ullamcorper a lacus vestibulum sed arcu non odio. Adipiscing commodo elit at imperdiet dui accumsan sit amet nulla. In est ante in nibh mauris cursus mattis. Nunc sed velit dignissim sodales ut eu sem. Volutpat diam ut venenatis tellus in metus vulputate. Aliquet nibh praesent tristique magna. Urna neque viverra justo nec. Scelerisque eu ultrices vitae auctor eu augue ut lectus. </li> \
    </div>',
		summary:  '<div style = "font-family: Arial Black;" class="my-class"> \
        <li>Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Sit amet porttitor eget dolor morbi non. Posuere sollicitudin aliquam ultrices sagittis orci a scelerisque. Euismod nisi porta lorem mollis aliquam ut porttitor leo. Enim nulla aliquet porttitor lacus. Praesent tristique magna sit amet. Nibh venenatis cras sed felis eget velit aliquet. Facilisis leo vel fringilla est ullamcorper. Feugiat nisl pretium fusce id. Elementum nibh tellus molestie nunc non. Semper eget duis at tellus at urna condimentum. Semper quis lectus nulla at volutpat. Duis convallis convallis tellus id interdum velit laoreet id donec. Integer eget aliquet nibh praesent tristique magna sit. Pharetra pharetra massa massa ultricies. Suspendisse interdum consectetur libero id faucibus nisl tincidunt eget. Dictum varius duis at consectetur. Sed ullamcorper morbi tincidunt ornare massa eget egestas purus. </li> \
			<li>Et malesuada fames ac turpis. Maecenas volutpat blandit aliquam etiam. Leo in vitae turpis massa. Massa eget egestas purus viverra accumsan in. Volutpat est velit egestas dui id ornare. Felis bibendum ut tristique et. Non quam lacus suspendisse faucibus interdum posuere. Dictum at tempor commodo ullamcorper a lacus. Augue neque gravida in fermentum. Elementum integer enim neque volutpat ac tincidunt. Scelerisque purus semper eget duis at. </li> \
			<li>Arcu bibendum at varius vel pharetra vel turpis. Turpis egestas pretium aenean pharetra magna ac. Ultricies mi quis hendrerit dolor. Eu facilisis sed odio morbi quis. Tempor commodo ullamcorper a lacus vestibulum sed arcu non odio. Adipiscing commodo elit at imperdiet dui accumsan sit amet nulla. In est ante in nibh mauris cursus mattis. Nunc sed velit dignissim sodales ut eu sem. Volutpat diam ut venenatis tellus in metus vulputate. Aliquet nibh praesent tristique magna. Urna neque viverra justo nec. Scelerisque eu ultrices vitae auctor eu augue ut lectus. </li> \
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

<!-- Nadpis "Správa knih" -->
<div class="header-container">
  <header>
    <h1>Správa knih</h1>
  </header>
</div>

<!-- Kontejner pro seznam knih a filtry -->
<body>
<div class="container">
  <!-- Seznam knih -->
  <div class="book-container">
    <div class="book-list-container">
      <div class="book-list">
        {#each books as book}
          <!-- Podmínka pro filtrování podle žánru -->
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

  <!-- Filtry pro žánry -->
  <div class="filter-container">
    <div
      style="
        background-color: #525e75;
        padding: 10px;
        border-radius: 30px;
        width: 300px;
      "
    >
      <p>
        <!-- Tlačítko pro zrušení filtru -->
        <button on:click={() => filterByGenre("")}>Zrušit filtr žánrů</button>
      </p>
      <!-- Žánry -->
      <p><button on:click={() => filterByGenre("román")}>Román</button></p>
      <p><button on:click={() => filterByGenre("elegie")}>Elegie</button></p>
      <p><button on:click={() => filterByGenre("povídka")}>Povídka</button></p>
      <p><button on:click={() => filterByGenre("legenda")}>Legenda</button></p>
      <p><button on:click={() => filterByGenre("komedie")}>Komedie</button></p>
    </div>
  </div>
</div>
</body>

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
    font-size: 4em; /* Velikost písma */
    font-family: "Arial Black";
    margin-top: 10px; /* Odsazení nadpisu od horního okraje */
    margin-left: 10px; /* Odsazení nadpisu od levého okraje */
    text-align: center;
    text-decoration: underline;
    color: #f1ddbf;
  }
</style>

