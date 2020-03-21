<script>
  export let ease, slide;
  let packOfLove = [];
  let unpuckedLove = [
    "meoew",
    "you're beautiful",
    "🌵 loves you",
    "🧡🧡🧡🧡🧡🧡🧡🧡🧡",
    "🦁 Tihon loves you",
    "🐈 Velik loves you",
    "You're awesome 💌",
    "🌵🌵🌵🌵🌵🌵",
    "^_^ meeeeeeeow",
    "don't worry, COVID-19 will be cured",
    "you're rock! ⛏️",
    "🌵 loves you",

    "You're the cutest kotya ❤️❤️❤️"
  ];
  let amountOfLove = 0;
  let isEnough = false;

  function showLove() {
    amountOfLove++;
    console.log(amountOfLove);

    if (amountOfLove < 10) {
      let randomItem =
        unpuckedLove[Math.floor(Math.random() * unpuckedLove.length)];
      packOfLove = [...packOfLove, randomItem];
    } else isEnough = true;
  }
</script>

<style>
  .meow-section {
    font-size: 24px;
  }
  .piece {
    margin-bottom: 5px;
  }

  .big {
    font-size: 34px;
    transform: scale(1);
    animation: pulse 3s infinite;
  }

  @keyframes pulse {
    0% {
      transform: scale(0.95);
    }

    70% {
      transform: scale(1);
    }

    100% {
      transform: scale(0.95);
    }
  }
</style>

<button
  transition:slide={{ delay: 350, duration: 1100, easing: ease }}
  on:click={showLove}>
  Press to be happy
</button>

<div class="meow-section">
  {#each packOfLove as pieceOfLove}
    <div class="piece">{pieceOfLove}</div>
  {/each}

  {#if isEnough}
    <p
      class="big"
      transition:slide={{ delay: 350, duration: 1100, easing: ease }}>
      Got enough love, lets share! 💚 🧡 ❤️ 💜
    </p>
  {/if}
</div>
