# The Secret Life of Objects

## A Vector Type

```js

class Vec {
  constructor(x, y) {
    this.x = x;
    this.y = y;
  }

  get length() {
    return Math.sqrt(this.x ** 2 + this.y ** 2);
  }

  plus(that) {
    return new Vec(this.x + that.x, this.y + that.y);
  }

  minus(that) {
    return new Vec(this.x - that.x, this.y - that.y);
  }
}

```

## Groups

```js

class Group {
  #members;

  constructor() {
    this.#members = [];
  }

  has(item) {
    return this.#members.includes(item);
  }

  add(item) {
    if (!this.#members.includes(item)) {
      this.#members.push(item);
    }
  }

  delete(item) {
    if (this.#members.includes(item)) {
      this.#members = this.#members.filter((member) => member !== item);
    }
  }

  static from(items) {
    const group = new Group();

    for (const item of items) {
      group.add(item);
    }

    return group;
  }
}

```

## Iterable Groups

```js

class Group {
  #members;

  constructor() {
    this.#members = [];
  }

  has(item) {
    return this.#members.includes(item);
  }

  add(item) {
    if (!this.#members.includes(item)) {
      this.#members.push(item);
    }
  }

  delete(item) {
    if (this.#members.includes(item)) {
      this.#members = this.#members.filter((member) => member !== item);
    }
  }

  static from(items) {
    const group = new Group();

    for (const item of items) {
      group.add(item);
    }

    return group;
  }

  [Symbol.iterator]() {
    let position = 0;
    
    return {
      next: () => {
        if (position < this.#members.length) {
          return {
            value: this.#members[position++],
            done: false,
          };
        } else {
          return { done: true };
        }
      },
    };
  }
}

```
