# JavaScript Code Explanation

## Variables Initialization

### randomNumber:
Generates a random number between 1 and 100 when the page loads.

### guesses, lastResult, lowOrHi:
Store references to HTML elements with specific classes for displaying game-related information.

### guessSubmit, guessField:
Store references to the submit button and input field for user interaction.

### guessCount:
Tracks the number of guesses the player has made.

### resetButton:
Used to create a button for starting a new game.

## Function checkGuess()

- Retrieves the user's guess from the input field.
- Updates the display with the user's guess and provides feedback if the guess is too high, too low, or correct.
- Handles the end of the game when the player wins or runs out of guesses.

## Event Listener for Guess Submission

Attaches the `checkGuess()` function to the submit button, so it runs when the player submits a guess.

## Function setGameOver()

- Disables the input field and submit button when the game ends.
- Creates a button to start a new game.
- Attaches the `resetGame()` function to the new game button.

## Function resetGame()

- Resets the game by clearing previous guesses and resetting the guess count.
- Enables the input field and submit button for a new game.
- Generates a new random number for the player to guess.

---

# DOM Manipulation Explanation

## Accessing DOM Elements

- The code utilizes `document.querySelector()` method to access specific elements in the HTML document by their class or tag names.
- For example, `document.querySelector('.guesses')` selects an element with the class name `guesses`.

## Updating DOM Content

- The code modifies the content of various HTML elements to reflect the game state and user interactions.
- For instance, `guesses.textContent += userGuess + ' ';` updates the content of an element with class `guesses` to display the user's guess.

## Changing CSS Styles

- The code dynamically changes CSS styles of elements to provide visual feedback to the user.
- For example, `lastResult.style.backgroundColor = 'green';` changes the background color of an element with class `lastResult` to green when the user guesses the correct number.

## Disabling and Enabling Form Elements

- The code disables and enables input fields and buttons to control user interactions and game flow.
- For instance, `guessField.disabled = true;` disables the input field to prevent further guesses after the game ends.

## Creating and Removing Elements

- The code creates new HTML elements and appends them to the document dynamically.
- For example, `resetButton = document.createElement('button');` creates a new `button` element, and `document.body.appendChild(resetButton);` appends it to the document body.

## Event Handling

- The code attaches event listeners to DOM elements to respond to user interactions.
- For example, `guessSubmit.addEventListener('click', checkGuess);` listens for clicks on the submit button and calls the `checkGuess()` function when clicked.
