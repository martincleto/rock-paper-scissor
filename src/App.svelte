<script>
  import rockIcon from './assets/rock-icon.svg';
  import paperIcon from './assets/paper-icon.svg';
  import scissorsIcon from './assets/scissor-icon.svg';

  let userChoice = null;
  let computerChoice = null;
  let result = null;

  const choices = ['rock', 'paper', 'scissors'];

  function play(choice) {
    userChoice = choice;
    computerChoice = choices[Math.floor(Math.random() * 3)];
    
    determineWinner();
  }

  function determineWinner() {
    switch (true) {
      case userChoice === computerChoice:
        result = 'Tie';
        break;
      case (userChoice === 'rock' && computerChoice === 'scissors') ||
          (userChoice === 'paper' && computerChoice === 'rock') ||
          (userChoice === 'scissors' && computerChoice === 'paper'):
        result = 'You win!';
        break;
      default:
        result = 'Computer wins';
    }
}

</script>

<div class="game">
  {#each choices as choice}
    <button on:click={() => play(choice)}>{choice}</button>
  {/each}
</div>

<div class="result">
  <!-- Display the user's and computer's choices, and the result -->
  {#if userChoice !== null}
    <p>Your choice: {userChoice}</p>
    <p>Computer's choice: {computerChoice}</p>
    <p>Result: {result}</p>
  {/if}
</div>

<style>
  /* Add your CSS styles here */
</style>


