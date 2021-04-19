<script>
  import { createEventDispatcher } from "svelte";
  export let name;
  export let id;

  let strike = false;

  const dispatch = createEventDispatcher();

  function removeTodo(id) {
    dispatch("remove", { id });
  }

  function strikeTodo() {
    strike = !strike;
  }
</script>

<li class="item" on:click={strikeTodo}>
  <div class={strike ? "item-name strike" : "item-name"}>
    <span>{name}</span>
    <span class="item-remove" on:click={() => removeTodo(id)}>
      <svg
        xmlns="http://www.w3.org/2000/svg"
        width="24"
        height="24"
        viewBox="0 0 24 24"
        fill="none"
        stroke="currentColor"
        stroke-width="2"
        stroke-linecap="round"
        stroke-linejoin="round"
        class="feather feather-x"
        ><line x1="18" y1="6" x2="6" y2="18" /><line
          x1="6"
          y1="6"
          x2="18"
          y2="18"
        />
      </svg>
    </span>
  </div>
</li>

<style>
  .item {
    list-style: none;
    margin: 0;
  }

  .item-name {
    padding: 1rem;
    font-size: 1.25rem;
    color: purple;
    background-color: white;
    font-weight: 600;
    border-bottom: 1px solid purple;
    display: flex;
    justify-content: space-between;
    align-items: center;
  }

  .item-remove {
    height: 1rem;
  }

  .strike {
    text-decoration: line-through;
  }
</style>
