# basic react hooks templates

## useEffect

### on dismount

```js
useEffect(
  () =>
    function dismount() {
      # do something on dismount
    },
  [],
);
```

### on first mount

```js
useEffect(() => {
  # do something on first mount
}, []);
```
