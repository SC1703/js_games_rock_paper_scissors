Hi developer,
I’d like a simple Rock, Paper, Scissors game built in vanilla JavaScript.

Here’s what I need:
I want 3 buttons to choose Rock, Paper, or Scissors.
The computer should pick one at random.
Show me the result: win, lose, or tie.
Keep track of the score: how many wins, losses, and ties I have.
A button to reset the score would be nice.
Keep the design clean and simple, but fun — it should be easy for anyone to play.

That’s it!
Thanks,
Your (imaginary) customer

# Rock, Paper, Scissors 🎮

A simple Rock, Paper, Scissors game built with vanilla JavaScript, HTML, and CSS.

## Features

- Player can choose Rock, Paper, or Scissors.
- Computer randomly selects Rock, Paper, or Scissors.
- Result is shown: Win, Lose, or Tie.
- Score tracking for wins, losses, and ties.
- Button to reset the score.

## User Interface

- Three buttons: Rock, Paper, Scissors.
- Text area (or card) to display:
  - Player’s choice
  - Computer’s choice
  - Result (Win/Lose/Tie)
- Scoreboard showing wins, losses, and ties.
- Reset button to clear the scoreboard.

## How to Play

1. Click one of the three buttons to make your choice.
2. The computer will randomly pick its choice.
3. The game will show the result and update the score.
4. Keep playing as long as you want, or click "Reset" to clear the score.

## Technologies

- HTML for structure
- CSS for styling
- JavaScript for game logic

## Future Improvements (optional)

- Add sounds or animations when a result is displayed.
- Keep a history of past rounds.
- Let the user play against a "best of 5" mode.

A global array with choices
a function called getComputerChoice that get the random number and assigns the element in the array at the generated index to a computerChoice variable and return it
lets

SET choices = ["rock", "paper", "scissors"]

FUNCTION getComputerChoice:
GENERATE random integer between 0 and 2
SET computerChoice = choices[random integer]
RETURN computerChoice

we first need the 3 buttons constants that get the buttons from the html elements the we need event listeners that have a playerChoice function attached to them that assings a playerChoice variable to a value corresponding to the pressed button the playerChoice function should return the playerChoice variable

SET playerChoice = null

GET buttonRock from HTML
GET buttonPaper from HTML
GET buttonScissors from HTML

FUNCTION handlePlayerChoice(choice):
SET playerChoice = choice
RETURN playerChoice

ADD event listener to buttonRock → calls handlePlayerChoice("rock")
ADD event listener to buttonPaper → calls handlePlayerChoice("paper")
ADD event listener to buttonScissors → calls handlePlayerChoice("scissors")

🔹 1. Return Statement in handlePlayerChoice

If the function only sets a global variable (playerChoice), a return isn’t strictly needed.

Example: event handlers don’t usually return values because the rest of the code doesn’t use them directly.

BUT if you want handlePlayerChoice to be more reusable (e.g., for testing or future extensions), having it return the chosen value can be helpful.

👉 For a simple game, it’s fine to skip the return.
👉 For a cleaner design, you might keep the return, even if it’s not used now.

🔹 2. Game Flow (Single Round vs Best of X)

This is more of a design requirement question. Since you’re building for the “customer”:

The customer’s request only mentioned single rounds (click → get result).

They didn’t ask for “best of 3/5” (though they did want score tracking).

So, I’d suggest:

Start with single rounds that automatically play when you click a button.

Later, you could add a best of 3/5 mode as a “Future Improvement” (already listed in your README 🎉).

That way you keep scope small at first (MVP), but you’ve left the door open for enhancements.

the playRound function takes the computerChoice and playerChoice as parameters it compares the playerChoice and computerChoice in an if else else if statement (example if player chose rock and computer chose scissors, player wins) and returns a winner (either player or computer)

FUNCTION playRound(playerChoice, computerChoice):
IF playerChoice == computerChoice:
RETURN "tie"

    ELSE IF playerChoice == "rock" AND computerChoice == "scissors":
        RETURN "player"

    ELSE IF playerChoice == "paper" AND computerChoice == "rock":
        RETURN "player"

    ELSE IF playerChoice == "scissors" AND computerChoice == "paper":
        RETURN "player"

    ELSE:
        RETURN "computer"

FUNCTION updateUI(winner, playerChoice, computerChoice):
IF winner == "tie":
DISPLAY "It's a tie! Both chose {playerChoice}"
ELSE IF winner == "player":
DISPLAY "Player wins! {playerChoice} beats {computerChoice}"
ELSE:
DISPLAY "Computer wins! {computerChoice} beats {playerChoice}"

2 text elements in the html, 1 for player score and 1 for computer score, we take those elements into the javascript file with something like getElementByID in the function handling the score we take the winner and use an if else statement to determine whose score we need to update by using the value returned by the playRound function
SET playerScore = 0
SET computerScore = 0
SET tieScore = 0 // (optional, if you want to display ties)

GET playerScoreElement from HTML
GET computerScoreElement from HTML
GET tieScoreElement from HTML (optional)

FUNCTION updateScore(winner):
IF winner == "player":
INCREMENT playerScore
UPDATE playerScoreElement with playerScore

    ELSE IF winner == "computer":
        INCREMENT computerScore
        UPDATE computerScoreElement with computerScore

    ELSE IF winner == "tie":
        INCREMENT tieScore
        UPDATE tieScoreElement with tieScore

resetScore function this function should set the playerScore, computerScore and tieScore variables to 0
FUNCTION resetScore:
GET resetButton from HTML
GET resultDisplayElement from HTML

FUNCTION resetScore:
SET playerScore = 0
SET computerScore = 0
SET tieScore = 0

    UPDATE playerScoreElement with 0
    UPDATE computerScoreElement with 0
    UPDATE tieScoreElement with 0

    CLEAR resultDisplayElement (set text to "")

ADD event listener to resetButton → calls resetScore
lets
