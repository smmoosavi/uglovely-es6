# uglovely-es6
ugly-lovely es6 syntax

## properties getter

input:
```js
const {color} = this.props;
```

output:
```js
var color = this.props.color;
```

**pros**
- Avoid duplicate name
- less code


## object creation

input:
```js
const color = 'red';
const size = 'small';
const o = {color, size};
```

output:
```js
var color = 'red';
var size = 'small';
var o = { color: color, size: size };
```

**pros**
- Avoid duplicate name
- less code sometimes

**cons**
- more code sometimes


## jsx props setter
input:
```jsx
const color = 'red';
<MyComponent {...{color}}/>;
```

equal to:
```jsx
const color = 1;
<MyComponent color={color}/>;
```

output:
```js
const color = 1;
React.createElement(MyComponent, { color: color });
```

**pros**
- Avoid duplicate name
- less code

