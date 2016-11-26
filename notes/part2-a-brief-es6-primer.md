## ES6

You'll see lots of stuff like

```javascript
import React from 'react';
import CoolComponent from './components/cool-component';
import handyLib from './utils/my-handy-lib'
```

☝ These are ES6 module import statements.

```javascript
export placeholderFunction
export default placeholderFunction
```

☝ These are ES6 module export statements. They tell ES6 which things in your file
should be made available to other files via `import`. The `default` one means that
you don't need to know the name of the thing when importing (and thus name it whatever
you like!)

```javascript
const group = 'ExchangeJS'
let name = 'Christian'
```

☝ These are constants and variables (respectively). They're both kinda like `var`, except
the `const` one denotes that it should not be changed later. In fact it will throw an
error if you try (handy!). It's best to use `const` for most things.

```javascript
const { prop1, prop2 } = this.props
```

☝ This is destructuring. It's pretty sweet. It sort of _pulls_ properties out of an object
and assigns them, so you can use `prop1` and `prop2` like normal constants later.

```javascript
const { prop1, prop2, ...rest } = this.props
```

☝ This is destructuring, but assigning all of the remaining properties to a new constant
called `rest` (can be named whatever you like). This is often referred to as "the rest
pattern"

```javascript
const sum = (a, b) => a + b
const sum = (a, b) => {
  return a + b
}
```

☝ These are arrow functions. In the first one, the `return` is implied and therefore
optional. The second one acts more like a traditional function definition. In both, the
value of `this` is inheritied from the enclosing scope. (No more `var self = this` etc)
