# uglovely-es6
ugly-lovely es6 syntax

basic:
- [properties getter](#properties-getter)
- [deep properties getter](#deep-properties-getter)
- [object creation](#object-creation)
- [pick](#pick)

a tempo up:
- [jsx props setter](#jsx-props-setter)
- [conditional object creation](#conditional-object-creation)
- [conditional array creation](#conditional-array-creation)


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


## deep properties getter

input:
```js
// action is {type: 'add', payload: {value: 1}}

const {type, payload: {value}} = action;
```

output:
```js
// action is { type: 'add', payload: { value: 1 } };

var type = action.type;
var value = action.payload.value;
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


## pick

input:
```js
// input is {size: 'large', color: 'red', text: 'es6'}
const {size, color} = input;
const output = {size, color};
```

output:
```js
// input is {size: 'large', color: 'red', text: 'es6'}
var size = input.size;
var color = input.color;
var output = { size: size, color: color };
```

**need help:**
is there any pure es6, one line, without name duplicated way?
```js
// lodash way
_.pick(input, ['size', 'color']);
```

**cons**
- duplicate name


## jsx props setter
input:
```jsx
const color = 'red';
<MyComponent {...{color}}/>;
```

equal to:
```jsx
const color = 'red';
<MyComponent color={color}/>;
```

output:
```js
const color = 'red';
React.createElement(MyComponent, { color: color });
```

**pros**
- Avoid duplicate name
- less code


## conditional object creation

input:
```js
const color = 'red';
const size = 'small';
const active = true; // or false

const o = {
    size,
    ...(active?{color}:{}),
}
```

equal logic:
```js
const color = 'red';
const size = 'small';
const active = true; // or false

const o = {size};
if (active) {
    o.color = color;
}
```

output:
```js
// ugly.
```

value:
```js
// active = true
o = {size: 'small', color: 'red'}

// active = false
o = {size: 'small'}
```

**pros**
- object creation is not flow of code
- no mutation

**cons**
- unfamiliar (yet)
- maybe a little performance

## conditional array creation

input:
```js
const holyday = true // or false
const tasks = [
    'wake up',
    'lunch',
    ...(holyday?[]:['work']),
    'sleep',
];
```

value:
```js
// holyday = true
tasks = ['wake up', 'lunch', 'sleep']

// holyday = false
tasks = ['wake up', 'lunch', 'work', 'sleep']
```


**pros**
- object creation is not flow of code
- no mutation

**cons**
- unfamiliar (yet)
- maybe a little performance
