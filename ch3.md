# Functions

## Minimum

```js

function min(a, b) {
  return (a < b) ? a : b;
}

```

## Recursion

```js

function isEven(n) {
  if (n < 0) {
    return isEven(-n);
  }

  if (n === 0) {
    return true;
  }

  if (n === 1) {
    return false;
  }

  return isEven(n - 2);
}

```

## Bean Counting

```js

function countChar(str, char) {
  let count = 0;

  for (let i = 0; i < str.length; i++) {
    if (str[i] === char) {
      count++;
    }
  }

  return count;
}

function countBs(str) {
  return countChar(str, 'B');
}

```

