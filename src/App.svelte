<script lang="ts">
  import Note from "./note.svelte";

  let notesList: any = [];

  retrieveLocalStorage();

  function addNote() {
    notesList = [...notesList, notesList.length + 1];
    saveNotesToStorage();
  }

  function deleteNote(index: number) {
    notesList.splice(index, 1);
    notesList = [...notesList];
    saveNotesToStorage();
  }

  function saveNotesToStorage() {
    localStorage.setItem("notesList", JSON.stringify(notesList));
  }

  function retrieveLocalStorage() {
    let newArray: any = localStorage.getItem("notesList");

    if (newArray)
    {
      notesList = JSON.parse(newArray)
    }
  }
</script>

<div class="center">
  <button on:click={addNote}>Add note</button>
</div>

{#each notesList as note, index (note)}
  <div class="note center">
    <button class="delete-button" on:click={() => deleteNote(index)}>&#128465;</button>
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

