<script>
  let task = "";
  let tasks = [];

  function addTask() {
    tasks = [...tasks, { id: Math.floor(Math.random() * 100), task }];
    task = "";
  }

  function deleteTask(id) {
    tasks = tasks.filter(task => task.id !== id);
  }
</script>

<style>
  h1 {
    text-align: center;
  }

  input {
    width: 100%;
  }

  button {
    color: white;
    background-color: blueviolet;
    width: 100%;
    cursor: pointer;
  }

  table,
  th,
  td {
    text-align: center;
  }

  .no__data {
    text-align: center;
    color: brown;
    font-size: 30px;
  }

  .btn__delete {
    color: white;
    background-color: red;
    width: 100%;
    cursor: pointer;
  }
</style>

<h1>Tasks</h1>
<form>
  <div>
    <label for="task">Task</label>
    <input type="text" id="task" bind:value={task} />
  </div>
  <button type="button" on:click={addTask} disabled={task === ''}>ADD</button>
</form>
<br />
{#if tasks.length}
  <table style="width:100%">
    <tr>
      <th>Id</th>
      <th>Task</th>
      <th>Delete</th>
    </tr>
    {#each tasks as task}
      <tr>
        <td>{task.id}</td>
        <td>{task.task}</td>
        <td>
          <button class="btn__delete" on:click={() => deleteTask(task.id)}>
            X
          </button>
        </td>
      </tr>
    {/each}
  </table>
{:else}
  <div class="no__data">No data !!!</div>
{/if}
