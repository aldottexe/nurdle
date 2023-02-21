<script>
   import Guess from './Guess.svelte';
   let guesses = [];
   let key = '3023672036'
   let won = false;

   let val = '';
   $: val = validateEntry(val);

   function validateEntry(val){
      if(val.length > 10 
         || val.charAt(val.length-1) < '0' 
         || val.charAt(val.length-1) > '9')
         return val.slice(0, val.length-1);
      return val;
   }

   function addNewGuess(e){
      e.preventDefault();
      if(val === key)
         won = true;

      guesses = [...guesses, val];
      val = '';
   }
</script>

<section class="win {won ? 'won':'hide'}">
   <h1>ggez</h1>
</section>

<h1>Nurdle</h1>
<p>For those who play hard to get.</p>

{#each guesses as guess}
<Guess key={key} guess={guess}></Guess>
{/each}

<form action="" on:submit={addNewGuess}>
   <input type="text" bind:value={val} />
   <Guess key="x" guess={val}></Guess>
   <input type="submit" hidden >
</form>

<style>
   *{
      color: white;
      font-family: "comic sans MS";
      text-align: center;
   }
   input{
      position: absolute;
      box-sizing: border-box;
      left: 0;
      opacity: 0%;
      width: 100vw;
      height: 100px;
   }
   form{
      padding-top: 7vh
   }
   .win{
      height: 100vh;
      width: 100vw;
      position:fixed;
      top:0;
      left: 0;
      display: flex;
      justify-content: center;
      align-items: center;
      background-color: rgba(94, 255, 201, 0.632);
      font-size: 3em;
      transition: opacity 1s;
   }
   .hide{
      opacity: 0;
      visibility: hidden;
   }
   .won{
      opacity: 100%;
   }
</style>