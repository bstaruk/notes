# js cheat sheet

a small collection of code snippets that can sometimes be useful for inspiration or reference.

### for loops
```js
for (let i = 0; i < items.length; i++) {
  items[i].classList.add('item--active');
}
```

### filter array of objects by key & value
```js
const needleId = 2;
const haystack = [{
  id: 1,
  title: 'Item 1'
}, {
  id: 2,
  title: 'Item 2'
}];

// logs: [{ id: 2, title: 'Item 2' }]
console.log(haystack.filter((o) => o.id === needleId));
```

### find the highest amount in array of objects
```js
const haystack = [{
  id: 1,
  amount: 100
}, {
  id: 2,
  amount: 200
}];

// logs: [{ id: 2, amount: 200 }]
console.log(
  haystack
    .map(o => o.amount)
    .reduce((a, b) => a > b ? a : b, 0);
);
```

### .contains
```js
const firstHaystack = document.querySelector('.haystack');
const firstNeedle = document.querySelector('.needle');

// checks if first haystack on the page is an ancestor of the first needle
console.log(firstHaystack.contains(firstNeedle));
```

[read more @ mdn](https://developer.mozilla.org/en-US/docs/Web/API/Node/contains)
