# CoffeeScript to ES6

A guide to migrate from CoffeeScript to ES6 / ES7 / ES2015

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
  // Static method that uses rest parameters
  static create (...args) {
    return new this(...args)
  }
  // Constructor that applies first argument to this.name
  constructor (name) {
    this._name = name
  }
  // Default value for name for class A
  get name () {
    return this._name || 'Default name for A'
  }
  // Necessary setter
  set name (value) {
    this._name = name
  }
}

class B extends A {
  // Default value for name for class B
  get name () {
    return this._name || 'Default name for B'
  }
}

let b1 = B.create()
alert(b1.name)

let b2 = B.create('ben')
alert(b2.name)
```

Notes:

- `arguments` is deprecated, use rest parameters instead:
  - [deprecation notice](https://groups.google.com/forum/embed/?place=forum/strengthen-js#!topic/strengthen-js/2lW_VzHBfKw)


## Traversing data object

``` coffee
data = {name:'ben', company:'bevry'}
for own key, value of data
  alert(key+': '+value)
```

``` javascript
let data = new Map().set('name', 'ben').set('company', 'bevry')
data.forEach(function(value, key){
  alert(key+': '+value)
})
```

Notes:

- using objects for data is deprecated, [Map](https://babeljs.io/docs/learn-es6/#map-set-weak-map-weak-set) is the new data object:
  - [deprecation and advisory notice](https://drive.google.com/file/d/0B1v38H64XQBNT1p2XzFGWWhCR1k/view) (see "Sane Objects" slide)


## Benchmarks

See [bevry/es6-benchmarks](https://github.com/bevry/es6-benchmarks) for performance benchmarks between ES5, CoffeeScript and ES6
