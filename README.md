# CoffeeScript to ES6

A guide to migrate from CoffeeScript to ES6/7/2015

## Classes

``` coffee
class A
  # Static method that uses rest parameters
  @create: (args...) -> new this(args...)
  
  # Constructor that applies first argument to this.name
  constructor: (@name) ->
  
  # Default value for name for class A
  name: 'Default name for A'

class B extends A
  # Default value for name for class B
  name: 'Default name for B'

b1 = B.create()
alert(b1.name)

b2 = B.create('ben')
alert(b2.name)
```

``` javascript
class A {
  # Static method that uses rest parameters
  static create (...args) {
    return new this(...args)
  }
  # Constructor that applies first argument to this.name
  constructor (name) {
    this._name = name
  }
  # Default value for name for class A
  get name () {
    return this._name || 'Default name for A'
  }
  # Necessary setter
  set name (value) {
    this._name = name
  }
}

class B extends A {
  # Default value for name for class B
  get name () {
    return this._name || 'Default name for B'
  }
}

let b1 = B.create()
alert(b1.name)

let b2 = B.create('ben')
alert(b2.name)
```
