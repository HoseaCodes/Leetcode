# Sort

The sort() method sorts the elements of an array in place and returns the sorted array. The default sort order is ascending, built upon converting the elements into strings, then comparing their sequences of UTF-16 code units values.

## How to sort strings

```js
const months = ["March", "Jan", "Feb", "Dec"];
months.sort();
console.log(months);
// expected output: Array ["Dec", "Feb", "Jan", "March"]
```

## How to sort nums

```js
const array1 = [1, 30, 4, 21, 100000];
array1.sort();
console.log(array1);
// expected output: Array [1, 100000, 21, 30, 4]
```

## How to sort numbers by value

```js
const array1 = [1, 30, 4, 21, 100000];
array1.sort((a, b) => a - b);
console.log(array1);
// expected output: Array [1, 4, 21, 30, 100000]

const numbers = [4, 2, 5, 1, 3];
numbers.sort((a, b) => a - b);
console.log(numbers);
// expected output: Array [1, 2, 3, 4, 5]
```

## How to sort an array of objects by comparing the value of one of their properties

```js
const items = [
  { name: "Edward", value: 21 },
  { name: "Sharpe", value: 37 },
  { name: "And", value: 45 },
  { name: "The", value: -12 },
  { name: "Magnetic", value: 13 },
  { name: "Zeros", value: 37 },
];

// sort by value
items.sort(function (a, b) {
  return a.value - b.value;
});

console.log(items);
// expected output: [
//   { name: 'The', value: -12 },
//   { name: 'Magnetic', value: 13 },
//   { name: 'Edward', value: 21 },
//   { name: 'Sharpe', value: 37 },
//   { name: 'Zeros', value: 37 },
//   { name: 'And', value: 45 }
// ]

// sort by charater
items.sort(function (a, b) {
  return a.name > b.name ? 1 : -1;
});
// expected output: [
//   { name: 'And', value: 45 },
//   { name: 'Edward', value: 21 },
//   { name: 'Magnetic', value: 13 },
//   { name: 'Sharpe', value: 37 },
//   { name: 'The', value: -12 },
//   { name: 'Zeros', value: 37 }
// ]
```
