# Property Descriptors

[Repl](https://repl.it/@vrezhhovanisyan/6lessonproperty#index.js)

```javascript
const user = {
  name: 'Vrezh',
  surname: 'Oganisyan',
  age: 22
}

Object.getOwnPropertyDescriptor(user, 'name');
```

## Writable

```javascript
const user = {
  name: 'Vrezh',
  surname: 'Oganisyan',
  age: 22
}

Object.defineProperty(user, "isDeveloper", {
  value: true,
  writable: false,
  configurable: true,
  enumerable: true,
});

user.isDeveloper = false;

console.log(user)
```

- `'use strict'`


## Configurable

_configurable is one-way action_

```javascript
const user = {
  name: 'Vrezh',
  surname: 'Oganisyan',
  age: 22
}

Object.defineProperty(user, "isDeveloper", {
  value: true,
  writable: false,
  configurable: false,
  enumerable: true,
});

user.isDeveloper = false;
console.log(user);

Object.defineProperty(user, "isDeveloper", {
  value: true,
  writable: false,
  configurable: true,
  enumerable: true,
});
```

- `delete` operator
- `'use strict'`


## Enumerable

  - hidden in `for .. in` loop

## Object Constant

- `writable: false`
- `configurable: false`

- Methods
  - `Object.freeze`
  - `Object.seal`
  - `Object.preventExtensions`

## Getters and Setters

```javascript
const user = {
  get name() {
    return user._name
  },
  set name(name) {
    user._name = name.trim()
    return name.trim()
  }
}
```
