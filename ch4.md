# Data Structures: Objects and Arrays

## The Sum of a Range

```js

function range(start, end, step = start < end ? 1 : -1) {
  const numbers = [];

  if (start < end && step > 0) {
    for (let n = start; n <= end; n += step) {
      numbers.push(n);
    }
  } else if (start > end && step < 0) {
    for (let n = start; n >= end; n += step) {
      numbers.push(n);
    }
  }

  return numbers;
}

```

```js

function sum(numbers) {
  let total = 0;

  for (const n of numbers) {
    total += n;
  }

  return total;
}

```

## Reversing an Array

```js

function reverseArray(arr) {
  const reversed = [];

  for (const item of arr) {
    reversed.unshift(item);
  }

  return reversed;
}

```

```js

function reverseArrayInPlace(arr) {
  for (let i = 0; i < Math.floor(arr.length / 2); i++) {
    const j = arr.length - i - 1;
    const temp = arr[i];
    arr[i] = arr[j];
    arr[j] = temp;
  }
}

```

## A List

```js

function arrayToList(arr) {
  if (arr.length === 0) {
    return null;
  }

  return { value: arr[0], rest: arrayToList(arr.slice(1)) };
}

```

```js

function listToArray(lst) {
  if (lst === null) {
    return [];
  }

  return prepend(lst.value, listToArray(lst.rest));
}

```

```js

function prepend(value, lst) {
  return { value, rest: lst };
}

```

```js

function nth(lst, n) {
  if (lst === null || n < 0) {
    return;
  }

  if (n === 0) {
    return lst.value;
  }

  return nth(lst.rest, n - 1);
}

```

## Deep Comparison

```js

function deepEqual(a, b) {
  if (typeof a !== typeof b) {
    return false;
  }

  if (typeof a !== 'object') {
    return a == b;
  }

  if (a === null || b === null) {
    return a == b;
  }

  const aKeys = Object.keys(a);
  const bKeys = Object.keys(b);

  if (aKeys.length !== bKeys.length) {
    return false;
  }

  for (let key of aKeys) {
    if (!bKeys.includes(key) || !deepEqual(a[key], b[key])) {
      return false;
    }
  }

  return true;
}

```
