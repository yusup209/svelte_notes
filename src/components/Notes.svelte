<script>
  import { db } from "../configs/firestore";
  import Note from './Note.svelte';

  let notes = [];

  db.collection("notes").orderBy('title').onSnapshot(data => {
    notes = data.docs;
  });
</script>

{#each notes as note}
  <Note id={note.id} note={note.data()} />
{/each}
