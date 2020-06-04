

<script>
  let lengthWanted = "";
  let numbers = false;
  let specialCharacters = false;
  let upperCase = false;
  let lowerCase = false;
  let finalPassword = "";
  const maxPasswordLength = 20;
  const minPasswordLength = 6;

  function generatePassword() {
    finalPassword = "";
    console.log("button was clicked...");

    if (lengthWanted > maxPasswordLength) {
      finalPassword = "Please have a lenght less than 20";
      return;
    } else if (lengthWanted < minPasswordLength) {
      finalPassword = "Please have a length greater than 6. ";
    } else if (
      upperCase === false &&
      specialCharacters === false &&
      numbers === false &&
      upperCase === false &&
      lowerCase === false
    ) {
      finalPassword = "Please select a checkbox";
    }
    generateLength();
  }

  function generateLength() {
    while (finalPassword.length < lengthWanted) {
      let pickCharacters =[]
      if (lowerCase) {
        console.log(`lower case is true`);
        let randomNumberLowerCase = Math.floor(Math.random() * 26) + 97;
        let pickLowerCase = String.fromCharCode(randomNumberLowerCase);
				pickCharacters = [...pickCharacters, pickLowerCase ]
        console.log(randomNumberLowerCase);
      }
      if (numbers) {
        console.log(`numbers is true`);
        let randomNumberNumbers = Math.floor(Math.random() * 10) + 48;
        let pickNumbers = String.fromCharCode(randomNumberNumbers);
        console.log(randomNumberNumbers);
				pickCharacters = [...pickCharacters,pickNumbers ]
      }
      if (specialCharacters) {
        console.log(`special characters is true`);
        let randomNumberSpecialCharacters = Math.floor(Math.random() * 4) + 35;
        let pickSpecialCharacters = String.fromCharCode(randomNumberSpecialCharacters);
        console.log(randomNumberSpecialCharacters);
			  pickCharacters = [...pickCharacters,pickSpecialCharacters ]
      }
      if (upperCase) {
        console.log(`upper case is true`);
        let randomNumberUpperCase = Math.floor(Math.random() * 26) + 65;
        let pickUpperCase = String.fromCharCode(randomNumberUpperCase);
        console.log(randomNumberUpperCase);
			  pickCharacters = [...pickCharacters,pickUpperCase ]
      }
			console.log(pickCharacters)

      console.log(finalPassword);
      let randomNumberPickCharacters = Math.floor(Math.random() * pickCharacters.length)+ 0;
      finalPassword += pickCharacters[randomNumberPickCharacters]
      console.log(pickCharacters[randomNumberPickCharacters])
            console.log(finalPassword);
    }
  }

  function resetPassword() {
    upperCase = false;
    lowerCase = false;
    specialCharacters = false;
    numbers = false;
    finalPassword = "";
    lengthWanted = "";
    console.log("")
  }
</script>

<section class="section content">
  <h1>Password Generator</h1>
  <label>
    Length:{lengthWanted}
    <input
      type="number"
      min="6"
      max="20"
      id="passwordlength"
      bind:value={lengthWanted} />
  </label>

  <label>
    Lowercase letters
    <input type="checkbox" id="uppercase" bind:checked={lowerCase} />

  </label>
  <label>
    Special Characters:
    <input type="checkbox" id="characters" bind:checked={specialCharacters} />
  </label>
  <label>
    Numbers:
    <input type="checkbox" id="characters" bind:checked={numbers} />
  </label>
  <label>
    Uppercase letters
    <input type="checkbox" id="uppercase" bind:checked={upperCase} />
  </label>

  <button
    class="button is-success is-outlined"
    id="generatepassword"
    on:click={generatePassword}>
    Generate Password
  </button>
  {finalPassword}
  {#if finalPassword !== ''}
    <button
      class="button is-danger is-outlined"
      id="resetpassword"
      on:click={resetPassword}>
      Reset
    </button>
  {/if}

</section>