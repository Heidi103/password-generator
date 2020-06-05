<script>
  // makes the variable lengthWanted equal 6
  let lengthWanted = 6;
  // makes the variable numbers equal false
  let numbers = false;
  // makes the variable specialCharacters equal false
  let specialCharacters = false;
  //makes the variable upperCase equal false
  let upperCase = false;
  // makes the variable lowerCase equal false
  let lowerCase = false;
  // makes the variable password equal nothing
  let password = "";
  // makes the minimum password length be 6
  let minPasswordLength = 6;
  // lets the maximum password length be 20
  let maxPasswordLength = 20;

  let output = "";
  console.log(lengthWanted);

  // a function to generate the password
  function validateInput() {
    // inside the generate password function final password always equals nothing at the start every time the function is run

    console.log("button was clicked...");

    //  if upperCase, specialCharacters, numbers and upperCase all equal false
    if (
      upperCase === false &&
      specialCharacters === false &&
      numbers === false &&
      upperCase === false &&
      lowerCase === false
      // an error message is outputted to the user telling them to select a checkbox
    ) {
      output = 'Please select a checkbox';
    }


  // calling the generatePassword function to be used
  else  {
    let finalPassword = generatePassword(
      lengthWanted,
      upperCase,
      specialCharacters,
      numbers,
      lowerCase
    );
    output = finalPassword;
  } 
  
  }

  // generateLength function
  function generatePassword(length, uCase, sCharacters, number, lCase) {
    // makes the minimum number for the lowercase from char code constantly be 97
    const minRandomNumberLowerCase = 97;
    // makes the range for both upper and lowercase letters in char code constantly be 26
    const rangeRandomNumberLetters = 26;
    // makes the minimum numbers for numbers in char code constandtly be 48
    const minRandomNumberNumbers = 48;
    // makes the range for numbers in char code constantly be 10
    const rangeRandomNumberNumbers = 10;
    // makes the minimum number for special characters in char code constantly be 35
    const minRandomNumberSpecialCharacters = 35;
    // makes the range for special characters in char code constantly be 4
    const rangeRandomNumberSpecialCharacters = 4;
    // makes the minimum number for uppercase letters in char code be 65
    const minRandomNumberUpperCase = 65;
    // makes the minimum number for the lowest number of an item in an array be 0
    const minNumberOfAnItemInAnArray = 0;

    let password = "";
    // while the length of password is less than the length wanted
    while (password.length < length) {
      // the array pickCharacters will be created
      let pickCharacters = [];
      // if lowerCase is true
      if (lCase) {
        // the variable randomNumberLowerCase will be equal to a randomly generated number from the between the minimum number for lowerCase letters from char code and the range of letters in char code which is 26 so a number will be generated between 97 and 122
        let randomNumberLowerCase =
          Math.floor(Math.random() * rangeRandomNumberLetters) +
          minRandomNumberLowerCase;
        // lets the variable pickLowerCase be equal to the randomly generated number of randomNumberLowerCase be converted from char code
        let pickLowerCase = String.fromCharCode(randomNumberLowerCase);
        // lets the variable pickLowerCase be added to the array called pickCharacters
        pickCharacters = [...pickCharacters, pickLowerCase];
      }
      // if numbers is true
      if (number) {

        // the variable randomNumberNumbers will be equal to a randomly generated number from the between the minimum number for numbers  from char code and the range of numbers in char code which is 10 so a number will be generated between 48 and 58
        let randomNumberNumbers =
          Math.floor(Math.random() * rangeRandomNumberNumbers) +
          minRandomNumberNumbers;
        // lets the variable pickNumbers be equal to the randomly generated number of randomNumberNumbers be converted from char code
        let pickNumbers = String.fromCharCode(randomNumberNumbers);
        // lets the variable pickNumbers be added to the array called pickCharacters
        pickCharacters = [...pickCharacters, pickNumbers];
      }
      if (sCharacters) {
        // the variable randomNumberSpecialCharacters will be equal to a randomly generated number from the between the minimum number for special characters  from char code and the range of special characters in char code which is 4 so a number will be generated between 35 and 39
        let randomNumberSpecialCharacters =
          Math.floor(Math.random() * rangeRandomNumberSpecialCharacters) +
          minRandomNumberSpecialCharacters;
        // lets the variable pickSpecialCharacters be equal to the randomly generated number of randomNumberSpecialCharacters be converted from char code
        let pickSpecialCharacters = String.fromCharCode(
          randomNumberSpecialCharacters
        );
        // lets the variable pickSpecailCharacters be added to the array called pickCharacters
        pickCharacters = [...pickCharacters, pickSpecialCharacters];
      }
      if (uCase) {
        console.log(`upper case is true`);
        // the variable randomNumberUpperCase will be equal to a randomly generated number from the between the minimum number for upper case letters  from char code and the range of uppercase letters in char code which is 26 so a number will be generated between 65 and 91
        let randomNumberUpperCase =
          Math.floor(Math.random() * rangeRandomNumberLetters) +
          minRandomNumberUpperCase;
        // lets the variable pickUpperCase be equal to the randomly generated number of randomNumberUpperCase be converted from char code
        let pickUpperCase = String.fromCharCode(randomNumberUpperCase);

        // lets the variable pickUpperCase be added to the array called pickCharacters
        pickCharacters = [...pickCharacters, pickUpperCase];
      }

      // lets the variable called randomNumberPickCharacters be equal toa  randomly generated number between the minimum number in an array which is zero and the length of the pickCharacters array
      let randomNumberPickCharacters =
        Math.floor(Math.random() * pickCharacters.length) +
        minNumberOfAnItemInAnArray;
      // the item selected from the pickCharacters array is added to the variable password each time the loop is repeated
      password += pickCharacters[randomNumberPickCharacters];
      console.log(pickCharacters[randomNumberPickCharacters]);
      console.log(password);
      console.log(length);
    }
    return password;
  }
  // a function to reset the setting on the password generator
  function resetPassword() {
    // upperCase is false
    upperCase = false;
    // lowerCase is false
    lowerCase = false;
    // specialCharacters is false
    specialCharacters = false;
    //numbers is false
    numbers = false;
    // password is equal to nothing
    output = "";
    // the length wanted is empty again
    lengthWanted = 6;

  }
</script>

<section class="section content">
  <!--Heading-->
  <h1>Password Generator</h1>
  <!--Creating checkboxes-->
  <label>
    Length:{lengthWanted}
    <input
      type="range"
      min={minPasswordLength}
      max={maxPasswordLength}
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
    on:click={validateInput}>
    Generate Password
  </button>
  {output}
  <!--If the variable password doesn't equal nothing-->
  {#if output !== ''}
    <!--A reset button that when clicked calls teh restPassword function which then resets all of the variables to their original value-->
    <button
      class="button is-danger is-outlined"
      id="resetpassword"
      on:click={resetPassword}>
      Reset
    </button>
  {/if}

</section>
