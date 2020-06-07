# This

_[...] `this` binding has nothing to do with where a function is declared, 
but instead has everything to do with a manner how the function is called_ (c) YDKJS

_[...] `this` is actually a bindind that is made when a function invoked_ (c) YDKJS


## Global `this`

## 'use strict'

## Call-site and four rules of determining this

- Call-site

```javascript
function fn() {
  console.log('Function #1');
  fn2();
}

function fn2() {
  console.log('Function #2');
}

fn2();
fn();
```

## The four rules

  ### Rule #1: Default binding

  ```javascript
  var str = 'Lorem ipsum';

  function fn() {
    console.log(this.str);
  }
  
  fn();
  ```
  
  ```javascript
  'use strict'
  
  var str = 'Lorem ipsum';

  function fn() {
    console.log(this.str);
  }
  
  fn();
  ```
  
  ### Rule #2: Implicit binding
  
  ```javascript
  function fn() {
    console.log(this.name);
  }

  const user = {
    name: 'Vrezh',
    fn: fn
  }
  
  user.fn();
  ```
  
  ```javascript
  function foo() {
    console.log(this.a);
  }

  const obj2 = {
    a: 2,
    foo: foo,
  }

  const obj1 = {
    a: 42,
    obj2: obj2
  };


  obj1.obj2.foo();
  ```

  ### Rule #2.1: Where's this? (Lost)

  ```javascript
  function fn() {
    console.log(this.name)
  }

  const user = { name: 'Vrezh', fn: fn }

  const fn2 = user.fn;

  var a = 'Ragnar';

  user.fn();
  fn2();
  ```

### Rule #3: Explicit Binding: `call`, `apply`, `bind`

```javascript
function fn() {
  console.log(this.name)
}

const user = {
  name: 'Vrezh'
}

fn.call(user);
fn.apply(user);
```

- Passing arguments

```javascript
function fn(arg1, arg2, arg3) {
  console.log(this.name)
}

const user = {
  name: 'Vrezh'
}

fn.call(user, 1, 2, 3);
fn.apply(user, [1, 2, 3]);
```

- `bind`

```javascript
function fn(arg1, arg2, arg3) {
  console.log(this.name)
}

const user = {
  name: 'Vrezh'
}

const callLater = fn.bind(user);

// some code...

callLater();
```

- Let's write our own bind using `apply`

### Rule #4: `new` Binding

- Default function call
- Constructor call

- When a function is invoked with `new`, following algorithm is working
  1. brand new object is being created
  2. `[[Prototype]]` linking with new object from step #1
  3. the newly created object is bound as `this` for the function call
  4. unless the function returns object, the newly constructed object from step #1 is being returned

```javascript
function fn (text) {
  this.arg = text
}

const instance = new fn('Lorem ipsum');
console.log(instance.arg)
```

### Determining `this`

1. if called with `new` => `this` equals to newly constructed object
2. if called with `call`, `apply`, `bind` => `this` equals to specified object
3. if the implicit binding happened => `this` equals to object context
4. otherwise =>
  - non-strict mode
    - `this` equals to `global` object
  - strict mode
    - `undefined`

## Arrow functions and `this`

```javascript
function foo() {
  return (a) => {
    console.log(this.a)
  }
}

const obj1 = { a: 2 }
const obj2 = { a: 3 }

const bar = foo.call(obj1)
bar.call(obj2)
```
