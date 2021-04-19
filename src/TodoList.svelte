<script>
  import Todo from "./Todo.svelte";

  let todos = [];
  let todoValue = "";

  function addTodo() {
    todoValue = todoValue.trim();

    if (!todoValue) return;

    const newTodo = {
      id: Date.now(),
      name: todoValue,
    };

    todos[todos.length] = newTodo;
    todoValue = "";
  }

  function removeTodo(e) {
    todos = todos.filter((todo) => todo.id !== Number(e.detail.id));
  }
</script>

<div class="list">
  <ul class="todos">
    {#each todos as item}
      <Todo name={item.name} id={item.id} on:remove={removeTodo} />
    {/each}
  </ul>

  <form on:submit|preventDefault={addTodo}>
    <input type="text" bind:value={todoValue} />
    <button>Add Todo</button>
  </form>
</div>

<style>
  .list {
    width: 100%;
    max-width: 400px;
    background-color: #d1d1d1;
    padding: 1rem;
  }

  .todos {
    padding: 0;
  }

  form {
    padding: 0.25rem;
    width: 100%;
  }
  input {
    margin: 0;
    width: 65%;
  }
  button {
    margin: 0;
    width: 25%;
  }
</style>
