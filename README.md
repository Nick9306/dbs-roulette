# DBS Roulette
Modified Version of Simply Roulette for use with Discord.

## Example Usage

```js
const Roulette = require('dbs-roulette');

// Create a new Table
const Table = new Roulette({ logging: true });

// Add Bets
// Params:  Player, Bet, Amount
Table.addBet('one', 'black', 110);
Table.addBet('two', '12', 56);

// Start the game to auto spin and produce events
Table.startGame();

// Event handler for every time the wheel spins automatically.
Table.on('spin', (winner) => {
  console.log('Wheel Results:', winner);
});
```

## Valid Bets

- `0` - `36` (Any single number from 0 to 36)
- `1-12` (1-12 means any number between and including the first dozen, 1-12)
- `13-24` (13-24 means any number between and including the second dozen, 13-24)
- `25-36` (25-36 means any number between and including the last dozen, 25-36)
- `black` / `red` (Bet on a colour black or red)
- `even` / `odd` (Any even or odd number)
- `1-18` (The first half of numbers)
- `19-36` (The last half of numbrs)

## Handling Betting

```js
// Send options when creating the Table
const Table = new Roulette({
  minimumBet: 100, // Default: 1
  maximumBet: 5000, // Default: 10000
// Max number of a bets a single player can make
  numberOfBets: 5 // Default: 3
});

// Add a Player Bet
Table.addBet('one', '30', 160);

// Edit Min/Max After the fact
Table.setMiniumBet(10);
Table.setMaxiumBet(10000);

// List All Bets
const allBets = Table.bets();
```

## Handling The Table

```js
// Creating a Table
const Table = new Roulette();

// Manually Spin
Table.spin()
  .then(winner => {
    console.log('RESULTS', winner);
  });

// Start an Auto-Spin (Spin's every minute)
Table.startGame();

// Handling Auto Spins
Table.on('spin', (winner) => {
  console.log('RESULTS', winner);
});

// Stop the Auto-Spin
Table.stopGame();
```
