## What is returned from the `useState` hook?
## What is the parameter for the `useState` hook?

An array containing the stateful variable, and a function to update the state.

```js
const [someState, setSomeState] = useState(someDefaultValue)

const someHook = useState(someDefaultValue)
const someState = someHook[0]
const setSomeState = someHook[1]
```

## Why would you pass a function as a component prop?

* To update the state from a child component
* Higher-order function

## Describe how to change state in a parent component from a child component.

Pass the setState function from the useState hook from the parent to a child via a prop.

## What is lifting state?

Moving state that's shared by siblings to a common ancestor

## How do you handle DOM events in React?
## What is the equivalent of `.addEventListener("click", handler)` in React?

In the regular DOM, you have events like `click`, `submit`, etc.
In React, you prefix these with `on` and give them a function

```jsx
<button onClick={someHandler}>Click Me!</button>
<SomeComponent onClick={someHandler} /> // Doesn't work
```

```jsx
<input onChange={() => setSomeState("Whatever")} /> // Right
<input onChange={setSomeState("Whatever")} />  // Wrong

const inputChangeHandler = name => event => {
  const newValue = event.target.value
  const handlers = {
    "first-name": (newValue) => setFirstName(newValue),
    "last-name": (newValue) => setLastName(newValue),
  }
  handlers[name](newValue)
}

<input name="first-name" onChange={inputChangeHandler("first-name")} />
<input name="last-name" onChange={inputChangeHandler("last-name")} />
<input name="age" onChange={inputChangeHandler("age")} />
<input name="income" onChange={inputChangeHandler("income")} />
```

## How do you prevent native form submissions in React?

```js
const handleSubmit = event => {
  event.preventDefault()
  // Rest of logic
}

<form onSubmit={handleSubmit}>
</form>
```

## How do you get the value of an input from its `change` event?

```js
event.target.value
```

## What data type does a event handler take in React?

Function

## Describe derivative state in your own words.

State that is derived from other state

```jsx
const [birthdate, setBirthdate] = useState("1984-01-01")
const age = calculateAge(birthdate)
```

## What is wrong with this code:

```js
useEffect(() => {
  if (someOtherConditionIsMet){
    const url = `https://pokeapi.co/api/v2/pokemon/${name}`
    fetch(url)
      .then(response => response.json())
      .then(pokemon => {
        setError(false)
        setPokemon(pokemon)
      }).catch(error => setError(true))
  }
}, [])
```

Missing the name in the dependency array

## What is a hook?

Hooks allow you to do certain React thingies without having to write a class for it. Thingies can be:

* State
* Effects
* Context

Some abstraction, potentially stateful, that can be consumed by a component.

## What is a side-effect?

Anything that effects something outside of the scope of the current function being executed.

## What is `useEffect` for?

Hook for managing side effects.

## What are the parameters of `useEffect`?

Function and a dependency array. The function will run when the component first renders, and then again whenever a watched variable in the array changes.

```js
useEffect(someEffectyFunction)                // Every render
useEffect(someEffectyFunction, [])            // Just once
useEffect(someEffectyFunction, [someValue])   // Initial, and every time someValue changes
```

## What is conditional rendering in React components?

Rendering code based on the result of an expression

```jsx
{someCondition
  ? <SomeComponent />
  : <SomeOtherComponent />
}

{someCondition &&
  <SomeComponent />
}

<div className={someCondition ? "user" : null}
```

```jsx
const SomeAsyncComponent = () => {
  const [ isLoading, setIsLoading ] = useState(false)
  const [ date, setDate ] = useState({})

  useEffect(() => {
    setIsLoading(true)

    fetch("someUrl")
      .then(parseResponse)
      .then(data => {
        setData(data)
      }).finally(() => {
        setIsLoading(false)
      })
  })

  return (
    <div>
      {isLoading
        ? <LoadingSpinner />
        : <YourCoolResult data={data} />
      }
    </div>
  )
}
```

## What does this render if `isOverdue` is `true` and `daysRemaining` is 3?

```jsx
{
  isOverdue
    ? <span className="alert badge">Overdue!</span>
    : <span className="badge">{daysRemaining} days remaining</span>
}
```

## What does this render if `isOverdue` is `true`?

```jsx
{
  isOverdue && <span className="alert badge">Overdue!</span>
}
```

## What does this render if `isOverdue` is `false`?

```jsx
{
  isOverdue && <span className="alert badge">Overdue!</span>
}
```
