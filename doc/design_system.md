# Design System

------

This document outlines the design system for the Yatzy lab.

# Fonts

------

## Primary Font: 

### Times New Roman

# Colours

------

## Primary Color:

- ### bisque

- ### aquamarine

## Secondary Color:

- ### Gold

- ### Gray

# Dice

------

The implementation of our dice is shown below:

## Function rollDice

**Parameter:** times (which specifes how many dice to roll)

**Return:** An array of integers indicate each dice's value

**Function body:** Using the `Math.random()` to generate an integer from 0 to 1, then using the `Math.floor()` to restrict the number from 1 to 6.

## Implementation:

```javascript
export const rollDice = (times) => {
  let dices = [];
  for (let i = 0; i < times; i++) {
    dices.push(Math.floor(Math.random() * 6) + 1);
  }
  return dices;
};
```

# Wordle

------

> We implement another game called <u>Wordle</u> instead of Yatzy.

## Game State

The Wordle has three states: playing, lost, won. The game will begin with the state playing until the player consumed all six chances. Then the game will either: restart after 3 seconds; or will turn into the lost state and restart the game again (change to the playing state).

## Game structure

We used the framework **Vue** to implement this game. The game board is packed inside a "container" `div` element. The game only have two parts: the header and the actual game board.

### Header

This section keeps the `give up` button which allow player to restart the game at any time, it will show the correct result once click on it. It also has a few components from the UI component library [PrimeVue](https://primevue.org/introduction/). Which is for the pop up window to display the answer, and alos for the pop up toasts, for better player experience.

### Game Board

The actual game board only has a 2D array which dynamically shows player's keyboards input. This is realized by `window.addEventListener('keydown', handleKeydown)` to bind each key stroke onto the array.

### Info

The section `info` is merely to display player's chances left, which is realized by Vue's `{{}}` syntax.

## Game End

When player correctly spell the word or waste all the chances, the game will either pop up a congratulation Toast or will warn the player game lost. Then the game will refresh the game board and enter the playing state again.	