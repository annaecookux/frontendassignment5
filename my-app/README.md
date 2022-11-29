Tutorial:
https://reactjs.org/tutorial/tutorial.html#setup-option-1-write-code-in-the-browser

What I did from the tutorial:

Load react
* Started by loading the react app in npx, and modifying the files to remove everything in src
* Created index.css and index.js and copy/pasted some base code into each, the js file pulls in a set of component subclasses and DOM native component (<button>)
* Loaded the app locally

Pass props, define state, and place state in higher level component
* Passed data through the props to fill each square with a number
* Create an onClick event listener, then establish state in squares so that they will render an “X” on click
* As it is, we have state rendering through individual squares, when we want it to render through the higher tier component, board. 
* So we change it so that when a square is clicked, it calls the board instead to receive it’s value. This will show errors until handleClick function is added
* We put in handleClick function to within board to now allow users to fill squares with “X” again. So the button state can either be null or “X”, but not “O” yet.
* We call .slice() to create a copy of the squares array to modify instead of modifying the existing array. This is called immutability which makes it easier to undo/redo actions, and detect state changes to determine when a component should be re-rendered.

Create boolean to allow for multiple players for “X” and “O”, provide feedback to user
* We add “O” as mark, but ensure that the first player is “X” by creating a boolean that flips each time a player clicks 
* Now we have null or “X” or “O”!
* Since players wouldn’t know whose turn it is unless they knew this logic, we show them whose turn it is by changing the render constant string

Declare winner
* To show who wins the game, the tutorial provides a helper function with the potential winning values defined in new function called calculateWinner,
* This is called in the boards render function as an if/else statement. 
* The winner is defined when the for loop reaches one of the values required, otherwise, the game continues with the next player taking their turn

Time travel
* Because have immutable states, we make it easy to revert back to previous steps in the game
* We store past squares arrays in a new array for our moves, a “history” state
* We place history in the Game component (which has been largely unused until now) because the history is a state affecting all other components. 
* So we have to lift up the squares state to the game component instead of board component to control the entirety of the board’s data. 

Show past moves
* We will use the arrays map method to map to other data from our selected buttons to our history display
* To ensure we can properly map changes, and that react understands what changes are made, we define keys.
* We will define step numbers that are identified with unique keys
* Note: this section started to lose me a little bit because of the jumping around in the code we are doing and the new term “keys.” They essentially sound like uniquely generated IDs used for each button so that React knows which button does what and when and doesn’t ever get them mixed up

It feels like I did a lot of thinking for not a lot of output but hey it works and I understand React a little better!

Questions:
* How does a screen reader know which option is selected and when? Is this accessible?
* Where is the visible focus state on each button? How do they get passed in with react?
