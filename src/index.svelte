<script>
  let lengthWanted = "";
  let letters = false;
  let numbers = false;
  let specialCharacters = false;
  let upperCase = false;
  let lowerCase = false;
  let finalPassword = "";
  let lengthOfPassword = 0;

  function checkLetters() {
    letters = true;
  }

  function checkNumbers() {
    numbers = true;
  }

  function checkSpecialCharacters() {
    specialCharacters = true;
  }

  function checkUpperCase() {
    upperCase = true;
  }
  function checkLowerCase() {
    lowerCase = true;
  }

  function generatePassword() {
    lengthOfPassword++;
    if (lowerCase) {
      let randomNumberLowerCase = Math.floor(Math.random() * 26) + 97;
      finalPassword += String.fromCharCode(randomNumberLowerCase);
      console.log(randomNumberLowerCase);

    }
    if (numbers) {
      let randomNumberNumbers = Math.floor(Math.random() * 10) + 48;
      finalPassword += String.fromCharCode(randomNumberNumbers);
      console.log(randomNumberNumbers);
    }
    if (specialCharacters) {
      let randomNumberSpecialCharacters = Math.floor(Math.random() * 4) + 35;
      finalPassword += String.fromCharCode(randomNumberSpecialCharacters);
      console.log(randomNumberSpecialCharacters);
    }
    if (upperCase) {
      let randomNumberUpperCase = Math.floor(Math.random() * 26) + 65;
      finalPassword += String.fromCharCode(randomNumberUpperCase);
      console.log(randomNumberSpecialCharacters)
    }

   if (upperCase === false && specialCharacters === false && numbers === false && upperCase === false && lowerCase === false)
   finalPassword = "Please select a checkbox"
    return;
  }
</script>

<section class="section content">
  <h1>Password Generator</h1>
  <label>
    Length:{lengthWanted}
    <input
      type="range"
      min="0"
      max="20"
      id="passwordlength"
      bind:value={lengthWanted} />
  </label>

  <label>
    Numbers:
    <input
      type="checkbox"
      id="characters"
      on:click={checkNumbers}
      bind:value={numbers} />
    Special Characters:
    <input
      type="checkbox"
      id="characters"
      on:click={checkSpecialCharacters}
      bind:value={specialCharacters} />
  </label>
  <label>
    Uppercase letters
    <input
      type="checkbox"
      id="uppercase"
      on:click={checkUpperCase}
      bind:value={upperCase} />
    Lowercase letters
    <input
      type="checkbox"
      id="uppercase"
      on:click={checkLowerCase}
      bind:value={lowerCase} />

  </label>
  <button
    class="button is-success is-outlined"
    id="generatepassword"
    on:click={generatePassword}>
    Generate Password
  </button>
  {finalPassword}
</section>
