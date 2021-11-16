## What is returned from the `useState` hook?

## What is the parameter for the `useState` hook?

## Why would you pass a function as a component prop?

## Describe how to change state in a parent component from a child component.

## What is lifting state?

## How do you handle DOM events in React?

## What is the equivalent of `.addEventListener("click", handler)` in React?

## How do you prevent native form submissions in React?

## How do you get the value of an input from its `change` event?

## What data type does a event handler take in React?

## Describe derivative state in your own words.

## What's wrong with this code:

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

## What is a hook?

## What is a side-effect?

## What is `useEffect` for?

## What are the parameters of `useEffect`?

## What is conditional rendering in React components?

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
