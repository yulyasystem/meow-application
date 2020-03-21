<script>
  import { fade } from "svelte/transition";
  import { quintOut } from "svelte/easing";
  import { slide } from "svelte/transition";
  import Happiness from "./Happiness.svelte";

  let name = "";
  let isShown = false;
  let isEmpty = true;
  function handleName(event) {
    let enteredValue = event.target.value;
    if (enteredValue.length !== 0) {
      isEmpty = false;
    } else isEmpty = true;
  }

  function showGreeting() {
    isShown = true;
  }
</script>

<style>
  .form {
    display: flex;
    flex-direction: column;
    text-align: left;
    margin: 0 auto;
    width: 300px;
  }

  .freak {
    font-size: 72px;
    background-image: linear-gradient(to right, #ffe600, #f0f);
    display: inline-block;
    background-clip: text;
    -webkit-text-fill-color: transparent;
  }

  h1 {
    letter-spacing: -6px;
    padding-bottom: 30px;
    margin-left: -12px;
  }

  label {
    margin-bottom: 5px;
  }
</style>

<header>
  {#if !isShown}
    <div transition:fade={{ delay: 100, duration: 100 }} class="form">
      <h1 class="freak">Julia, you are fucking freak</h1>
      <label>What is your name?</label>
      <div class="submit">
        <input type="text" bind:value={name} on:input={handleName} />
        <button on:click={showGreeting} disabled={isEmpty}>Okay</button>
      </div>

    </div>
  {/if}

  {#if isShown}
    <h1 transition:slide={{ delay: 150, duration: 1500, easing: quintOut }}>
      Hello, {name}!
    </h1>
    <Happiness {slide} ease={quintOut} />
  {/if}
</header>
