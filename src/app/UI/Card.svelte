<script>
  import { createEventDispatcher } from "svelte";
  import { fade } from "svelte/transition";

  const dispatch = createEventDispatcher();

  export let id;
  export let title = "";
  export let newCard = false;

  let introtime = 400;
  let outrotime = newCard ? 0 : 400;

  function deleteCardDispatcher() {
    dispatch("deleteCard", id);
  }
</script>

<article
  id="{id}"
  class:newCard
  in:fade="{{ duration: introtime }}"
  out:fade="{{ duration: outrotime }}">
  <h3 class:newCardTitle="{newCard}">
    {title}
    <button on:click="{deleteCardDispatcher}"> x </button>
  </h3>

  <slot>Empty Card</slot>
</article>

<style lang="scss">
  article {
    min-width: 200px;
    margin: 0.5rem;
    background-color: $lightblue;
    border-radius: 0.4rem;
    position: relative;
  }
  h3 {
    padding: 0.5rem 0;
    text-align: center;
    color: $color-2;

    &:hover button {
      visibility: visible;
    }
  }
  button {
    position: absolute;
    top: 0.5rem;
    right: 0.5rem;
    padding: 0 0.4rem;
    color: white;
    background-color: rgb(167, 0, 0);
    border-radius: 0.4rem;
    border: none;
    visibility: hidden;
  }
  .newCard {
    background-color: $color-2;
  }
  .newCardTitle {
    color: white;
  }
</style>
