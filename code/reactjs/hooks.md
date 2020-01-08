# basic react hooks templates

### useEffect

https://reactjs.org/docs/hooks-effect.html

#### on dismount

```js
useEffect(
  () =>
    function dismount() {
      /* do something on dismount */
    },
  [],
);
```

#### on first mount

```js
useEffect(() => {
  /* do something on first mount */
}, []);
```

#### on first mount, and when a specific prop changes

```js
useEffect(() => {
  /* do something on first mount, and when exampleProp changes */
}, [exampleProp]);
```


#### every time the component re-renders

```js
useEffect(() => {
  /* do something on every re-render */
});
```

---

### useState

https://reactjs.org/docs/hooks-state.html

#### basic state variable & setter

```js
const [success, setSuccess] = useState(false);
```
