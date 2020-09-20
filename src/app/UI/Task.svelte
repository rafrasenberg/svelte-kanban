<script>
  import { createEventDispatcher, onMount } from "svelte";
  import { slide } from "svelte/transition";

  const dispatch = createEventDispatcher();

  export let id;
  export let value = "New Task";
  export let firstCard = false;
  export let lastCard = false;

  let thisInput;

  function insertTaskDispatch() {
    dispatch("blurred", { value: value, id: id });
  }

  function deleteTaskDispatch() {
    dispatch("deleteTask", id);
  }

  function moveLeftDispatch() {
    dispatch("moveLeft", { value: value, id: id });
  }

  function moveRightDispatch() {
    dispatch("moveRight", { value: value, id: id });
  }

  onMount(() => {
    thisInput.focus();
  });
</script>

<label transition:slide>
  <input
    id="{id}"
    type="text"
    placeholder="Insert task..."
    bind:value
    bind:this="{thisInput}"
    on:blur="{insertTaskDispatch}" />
  <button id="btnClose" on:click="{deleteTaskDispatch}"> x </button>

  {#if !firstCard}
    <button id="btnLeft" class="btnArrow" on:click="{moveLeftDispatch}">
      ←
    </button>
  {/if}

  {#if !lastCard}
    <button id="btnRight" class="btnArrow" on:click="{moveRightDispatch}">
      →
    </button>
  {/if}
</label>

<style lang="scss">
  label {
    position: relative;
    padding: 1.45rem 0.5rem;
  }
  input {
    width: 100%;
    margin: 0;
    padding: 0.2rem;
    background: white;
    color: #333;
    border-radius: 0.2rem;
    // transition: background-color 200ms linear;
  }
  button {
    position: absolute;
    visibility: hidden;
    z-index: 3;
    margin: 0;
  }
  label:hover button {
    visibility: visible;
  }
  #btnClose {
    top: -0.05rem;
    right: 0.45rem;
    padding: 0 0.4rem;
    color: rgb(167, 0, 0);
    background-color: #f4f4f4;
  }
  #btnClose:not(:disabled):active {
    background-color: rgb(167, 0, 0);
    color: #f4f4f4;
  }
  .btnArrow {
    bottom: -0.05rem;
    padding: 0.2rem 2rem 0.4rem 2rem;
    color: $color-2;
    background-color: #f4f4f4;
    font-size: 2rem;
    line-height: 0.8rem;
  }
  .btnArrow:not(:disabled):active {
    background-color: $color-2;
    color: #f4f4f4;
  }
  #btnRight {
    right: 0.45rem;
  }
  #btnLeft {
    left: 0.45rem;
  }
</style>
