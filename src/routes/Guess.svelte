<script>
   export let guess;
   export let key;

   function parseColor(i){
      let guessChar = guess.charAt(i);

      if(guessChar === '')
         return '';

      if (guessChar === key.charAt(i))
         return 'green';

      if(key.indexOf(guessChar) != -1)
         return 'yellow';

      return '';
   }

</script>

<div>
   <h3>(</h3>
   <h3 class="letter {parseColor(0)}">{guess.charAt(0)}</h3>
   <h3 class="letter {parseColor(1)}">{guess.charAt(1)}</h3>
   <h3 class="letter {parseColor(2)}">{guess.charAt(2)}</h3>
   <h3>)</h3>
   <h3 class="letter {parseColor(3)}">{guess.charAt(3)}</h3>
   <h3 class="letter {parseColor(4)}">{guess.charAt(4)}</h3>
   <h3 class="letter {parseColor(5)}">{guess.charAt(5)}</h3>
   <h3>-</h3>
   <h3 class="letter {parseColor(6)}">{guess.charAt(6)}</h3>
   <h3 class="letter {parseColor(7)}">{guess.charAt(7)}</h3>
   <h3 class="letter {parseColor(8)}">{guess.charAt(8)}</h3>
   <h3 class="letter {parseColor(9)}">{guess.charAt(9)}</h3>
</div>

<style>
   *{
      color: white;
      font-family: "comic sans MS";
   }
   div{
      display: flex;
      width: fit-content;
      margin: 20px auto;
   }
   div *{
      width: 2em;
      height: 2em;
      text-align: center;
      margin: 3px;
      padding-top: 3px;
      box-sizing: border-box;
   }
   .letter{
      border: 2px solid rgba(255, 255, 255, 0.3);
   }
   .yellow{
      background-color: darkgoldenrod;
   }
   .green{
      background-color: darkcyan;
   }
</style>