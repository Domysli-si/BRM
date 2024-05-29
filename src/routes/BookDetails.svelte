<script>
  export let book;
</script>

<div class="book">
  <div class="book-title">{book.title}</div>
  <div class="book-details">
    <div><strong>Autor:</strong> {book.author}</div>
    <div><strong>Rok vydání:</strong> {book.year}</div>
    <div><strong>Žánr:</strong> {book.genre}</div>
    <div class="book-description">
      <p>Popis knihy může být zde...</p>
    </div>
  </div>
</div>

<style>
  .book {
    background-color: #525e75;
    padding: 20px;
    border-radius: 10px;
  }
  .book-title {
    font-size: 2em;
    text-align: center;
    text-decoration: underline;
    color: #f1ddbf;
  }
  .book-details {
    margin-top: 20px;
    font-size: 1.2em;
  }
  .book-description {
    margin-top: 20px;
    font-size: 1em;
    line-height: 1.5;
  }
</style>
