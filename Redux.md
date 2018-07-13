# Redux

## Core Principles

- The whole state of your app is stored in an object tree inside a single store.
- The only way to change the state tree is to emit an action, an object describing what happened.
- To specify how the actions transform the state tree, you write pure reducers.

## Why Redux?
- One Store
- Reduced Boilerplate
- Isomorphic/Universal Friendly
- Immutable Store
- Hot Reloading
- Time-travel debugging
- Small

## Reducer
A reducer is a function build to decide how every action transforms the entire application's state.
A reducer is a pure function with (state, action) => state signature

### States
The only way to mutate the internal state is to dispatch an action.

A state can be:
- a primitive
- an array
- an object
- an Immutable.js data structure

```javascript
function counter(state = 0, action) {
  switch (action.type) {
  case 'INCREMENT':
    return state + 1
  case 'DECREMENT':
    return state - 1
  default:
    return state
  }
}
```

## Store
Stores are used to hold the state of your app. Its API is { subscribe, dispatch, getState }.

```javascript
let store = createStore(counter)
```

## Actions
Instead of mutating the state directly, you specify the mutations you want to happen with plain objects called actions.
The actions can be serialized, logged or stored and later replayed.

```javascript
store.dispatch({ type: 'INCREMENT' }) // 1
store.dispatch({ type: 'INCREMENT' }) // 2
store.dispatch({ type: 'DECREMENT' }) // 1
```


## Differences with Flux
- Redux doesn't have a Dispatcher
- Redux doesn't support many stores
- There is just a single store with a single root reducing function
- Instead of adding stores, you split the root reducer into smaller reducers
