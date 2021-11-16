## What does `{}` do in JSX?

Indicates that the code inside the `{}` needs to be evaluated as JS and potentially rendered

## What's wrong with this JSX: `<img src="{imageUrl}" alt="descriptive text" />`?

`"{imageUrl}"` renders as a string.

## How you do you include a component in a JSX template?

Import the component, use it as `<ComponentName props />` or `<ComponentName><p>Anything we want here</p></Component>`

Access the children with `props.children`

## What is a prop?

Property on a component, a value passed in.

* Primitive
* Objects
* Functions
* Classes
* Components

## What is the syntax for giving a component a prop?

```jsx
<Component propName={something} />
<Component propName="Something" />
<Component propName={true} />
<Component
  propName={{
    someProperty: "Some Value",
    anotherProperty: "Another Value"
  }}
  anotherProp={anotherProp}
  yetAnotherProp={yetAnotherProp}
/>

//

<button onClick={event => setSomeState(event.target.value)}>Some Button</button>

const clickHandler = event => setSomeState(event.target.value)
<button onClick={clickHandler}>Some Button</button>

```

## What is the syntax for receiving a prop from a component?

```jsx
const MyComponent = (props) => {
  return (
    <SomeCoolWrapper {...props}>
      {...children}
    </SomeCoolWrapper>
  )
}
const MyComponent = ({ subProp1, subProp2 }) => { componetBody }
```

## What is the purpose of destructuring?

Declare variables directly from an object without having to reference each property directly.

## How do you export a module from a file?

```js
// Part of JavaScript (now)
import Whatever from "./whatever"
import { Whatever } from "./whatever"

export default SomeThing // Default Export
export SomeThing         // Named Export
```

```js
// Used through Node
const Whatever = require("./whatever")
const { Whatever } = require("./whatever")

module.exports = SomeThing
module.exports.SomeThing = SomeThing
```

```js
import { map, reduceRight, intersection, chain } from "lodash"
```

## When does an arrow function need to wrap its parameters in parentheses?
## When can an arrow function wrap its parameters in parentheses?

* 0 parameters
* 2 or more parameters
* If we're destructuring an object

(Optional for 1)

```js
function a(){
  return function b(){
    return function c(){
      return "Hi"
    }
  }
}

const a => b => c => "Hi"
```

## What is a ternary expression?

Different way of writing `if`/`else`

```js
ifSomething ? true : false

ifSomething
  ? true
  : false

ifSomething
  ? ifSomethingElse
    ? true
    : false
  : false
```

## What is spreading?

Copying an array or object, used to pass props to other components.

```
const someArray = [1, 2, 3]
const someObject = {
  a: 1,
  b: 2,
  c: 3,
}

someFunction(...someArray) // Same as someFunction(1, 2, 3)
const someOtherObject = {
  ...someObject,
  b: 45, // Clobbering
  d: 4,
}
```

```js
const kyle = {
  name: "Kyle",
  instrument: {
    manufacturer: "Epiphone",
    make: "ES355"
  }
}

const copyOfKyle = {
  ...kyle
}

copyOfKyle.name = "Duncan"
copyOfKyle.instrument.make = "Sheraton"

const deepCopyOfKyle = JSON.parse(JSON.stringify(kyle))
```

## What are keys used for in JSX and why can't indexes be used as keys?

* Need to uniquely identify each element
* Index isn't unique to that element- array can be reordered

## How do you turn a list of items into a list of JSX elements?

Using the `map` function.

```jsx
const pokemonNames = ["pikachu", "bulbasaur", "charmander"]

return (
  <ul>
    {pokemonNames.map(pokemonName => (
      <li key={pokemonName}>{pokemonName}</li>
    ))}
  </ul>
)
```

## What is state?

Anything that's persistent knowledge about a component or application that can change

## How is state declared in a React component?

```jsx
import { useState } from "react"

function SomeComponent() {
  const [myState, setMyState] = useState(myInitialValue)
}
```
