# Higher-Order Functions

## Flattening

```js

function flatten(arrays) {
  return arrays.reduce((flat, array) => flat.concat(array), []);
}

```

## Your Own Loop

```js

function loop(start, test, update, action) {
  for (let i = start; test(i); i = update(i)) {
    action(i);
  }
}

```

## Everything


```js

function every(array, test) {
  for (const item of array) {
    if (!test(item)) {
      return false;
    }
  }

  return true;
}

```

```js

function every(array, test) {
  return !array.some(item => !test(item));
}

```
