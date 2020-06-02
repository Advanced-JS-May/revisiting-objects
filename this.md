# This

_[...] `this` binding has nothing to do with where a function is declared, 
but instead has everything to do with a manner how the function is called_ (c) YDKJS

_[...] `this` is actually a bindind that is made when a function invoked_ (c) YDKJS


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
  
  const obj1 = {
    a: 42,
    foo: foo,
  };
  
  const obj2 = {
    a: 2,
    obj2: obj2
  }
  
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

### Rule #3: Explicit Binding: call, apply, bind

  
- new

- window

- use strict
