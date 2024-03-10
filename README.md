# Eloquent JavaScript

My Solutions to Exercises in Eloquent JavaScript (4th Edition)

## Program Structure

### Looping a Triangle

```js

for (let line = '#'; line.length < 8; line += '#') {
  console.log(line);
}

```

### FizzBuzz

```js

for (let n = 1; n <= 100; n++) {
  let word = '';

  if (n % 3 == 0) {
    word += 'Fizz';
  }

  if (n % 5 == 0) {
    word += 'Buzz';
  }

  console.log(word || n);
}

```

### Chessboard

```js

const size = 8;

let board = '';

for (let row = 0; row < size; row++) {
  for (let col = 0; col < size; col++) {
    if ((row + col) % 2 == 0) {
      board += ' ';
    } else {
      board += '#';
    }
  }

  // remove redundant new line character
  if (row < size - 1) {
    board += '\n';
  }
}

console.log(board);

```




