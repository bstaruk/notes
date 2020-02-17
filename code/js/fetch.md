# fetch copy-and-paste'ables

### fetch function: local w/ simulated network delay:
```javascript
const jsonData = require('./jsonData.json');
const postDataLocal = (payload) => {
  'console' in window && console.log('postDataLocal', payload);
  return new Promise((resolve) => {
    setTimeout(() => {
      resolve(jsonData);
    }, 1500);
  });
};
```

### remote post w/ json response:
```javascript
const postData = (payload) => (
  fetch('/path/to/api', {
    credentials: 'include',
    method: 'POST',
    body: JSON.stringify(payload)
  })
    .then((r) => r.json())
    .then((data) => data)
);
```

### fetch method utilization:
```javascript
postData(payload).then(
  data => {
    _doSomething(data);
  }
).catch(
  data => {
    _doSomethingElse(data);
  }
);
```
