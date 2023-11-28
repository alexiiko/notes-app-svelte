<script lang="ts">
  import Note from "./note.svelte";

  let notesList: any = []

  function addNote()
  {
    let key: number = notesList.length + 1
    notesList = [...notesList, { key }]
  }

  function deleteLastNote()
  {
    notesList.pop()
  }
</script>


<main>
  <div>
    <button on:click={addNote}>Add note</button>
    <button on:click={deleteLastNote}>Delete last note</button>
  </div>

  {#each notesList as {key}}
    <div>
      <Note />
    </div>
  {/each}       
</main>

