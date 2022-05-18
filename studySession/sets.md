# Set

How to create a set:

```js
let set1 = new Set();
```

How to get the size of a set:

```js
set1.size;
```

- The counting starts from 1 not 0 (like arrays)

How to add a value to a set:

```js
set1.add(42);
```

Chaining add vaules to set

```js
set1.add({ x: 10, y: 20 }).add({ x: 20, y: 30 });
```

How to iterate through a set:

```js
for (let item of set1) {
  console.log(item);
}
```

Alternatively

```js
let setIterator = set1[Symbol.iterator]();
// Returns the first value in set
console.log(setIterator.next().value);
// Returns the second value in set
console.log(setIterator.next().value);
// ... shows the next few vaules
```

Other alternative

```js
let setIterator1 = set1.values();
console.log(setIterator.next().value);
// Returns the second value in set
```

How to remove all elements in a set:

```js
set1.clear();
```

How to remove a specific value

```js
set1.delete(42);
```

How to turn a set into an object that an array of values:

```js
let set = new Set();
set.add(42)
set.add('forty two')
// The object
let iterator1 = set.entries();
// Inside of the object is an array
for (let entry of iterator1) {
    console.log(entry);
    // expected output: [42, 42]
    // expected output: ["forty two", "forty two"]}
```

How to find out if a value is with in the specified value exists in a set:

```js
set1.has(1);
// expected output: false
```
