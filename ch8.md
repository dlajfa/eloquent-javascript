# Bugs and Errors

## Retry

```js

class MultiplicatorUnitFailure extends Error {}

```

```js

function primitiveMultiply(a, b) {
  if (Math.random() < 0.2) {
    return a * b;
  } else {
    throw new MultiplicatorUnitFailure("Klunk");
  }
}

```

```js

function reliableMultiply(a, b) {
  while (true) {
    try {
      return primitiveMultiply(a, b);
    } catch (error) {
      if (!(error instanceof MultiplicatorUnitFailure)) {
        throw error;
      }
    }
  }
}

```

## The Locked Box

```js

const box = new (class {
  locked = true;
  #content = [];

  unlock() {
    this.locked = false;
  }

  lock() {
    this.locked = true;
  }

  get content() {
    if (this.locked) throw new Error("Locked!");
    return this.#content;
  }
})();

```

```js

function withBoxUnlocked(action) {
  const locked = box.locked;

  if (locked) {
    box.unlock();
  }

  try {
    action();
  } finally {
    if (locked) {
      box.lock();
    }
  }
}

```

