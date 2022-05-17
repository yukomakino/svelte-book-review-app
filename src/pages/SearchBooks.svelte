<script lang="ts">
  import BookCard from '../components/BookCard.svelte'
  import { books } from '../store/book'
  import { onDestroy } from 'svelte'
  import type { BookItem } from '../repositories/book'

  let _books: BookItem[]

  const unsubscribe = books.subscribe(value => _books = value)

  onDestroy(unsubscribe)
</script>

<div class="grid grid-cols-1 gap-2 lg:grid-cols-2">
  {#each _books as book (book.id)}
    <BookCard {book} />
  {/each}
</div>