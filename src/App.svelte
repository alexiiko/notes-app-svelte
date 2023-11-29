<script lang="ts">
  import Note from "./note.svelte";

  let notesList: any = []

  function addNote()
  {
    notesList = [...notesList, notesList.length + 1]
  }

  function deleteNote(index: number)
  {
    notesList.splice(index, 1)
    notesList = [...notesList]
  }
</script>


<div class="center">
  <button on:click={addNote}>Add note</button>
</div>

{#each notesList as note, index (note)}
  <div class="note center">
    <button class="delete-button" on:click={() => deleteNote(index)}>&#128465</button>
    <Note />
  </div>
{/each}       


<style>
  .note {
    display: flex;
    align-items: center;
  }

  .delete-button {
    margin-right: 8px;
  }

  .center {
    display: flex;
    justify-content: center;
  }
</style>
