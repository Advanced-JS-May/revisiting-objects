# Prototype

_Note, I'd recommend to check all examples in pythontutor_

_Note, materials of this lesson based on Dan Abramov's [newsletter](https://justjavascript.com/)_ 

[Code Examples](https://repl.it/@vrezhhovanisyan/6lessonprototype#index.js)

## Property and method

## What?

```javascript
const user = { name: 'Vrezh' };
console.log(user.isHuman); // ??? true ???
```

## \_\_proto\_\_

```javascript
const person = { isHuman: true };
const user = { name: 'Vrezh', __proto__: person }
console.log(user.isHuman); // true
```

## Shadowing

```javascript
const person = { isHuman: true };
const chewbacca = { isHuman: false, __proto__: person };
console.log(chewbacca.isHuman); ???
```

## Object.hasOwnProperty

```javascript
const person = { isHuman: true };
const user = { name: 'Vrezh', __proto__: person }
console.log(user.hasOwnProperty('isHuman')); // false
console.log(person.hasOwnProperty('isHuman')); // true
```

```javascript
const person = { isHuman: true };
const chewbacca = { isHuman: false, __proto__: person };
console.log(user.hasOwnProperty('isHuman')); // true
console.log(person.hasOwnProperty('isHuman')); // true
```

## Assignment

```javascript
const person = { isHuman: true };
const user = { name: 'Vrezh', __proto__: person }
user.isHuman = false
console.log(person.isHuman);
console.log(user.isHuman);
```

## Built-in Object prototype


```javascript
const user = { name: 'Vrezh' };
console.log(user.__proto__);
```

## Empty __proto__

```javascript
const user = { name: 'Vrezh', __proto__: null };
console.log(user.__proto__);
```


## Different object's sharing the same prototype

```javascript
const person = {
  isHuman: true,
  hasAge: true,
};

const user1 = { name: 'Elon', __proto__: person };
const user2 = { name: 'Adele', __proto__: person };

user1.__proto__.isHuman = false;

console.log(user1.isHuman)
console.log(user2.isHuman)
```

## Object.create
