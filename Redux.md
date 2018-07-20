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


## Differences with Flux
- Redux doesn't have a Dispatcher
- Redux doesn't support many stores
- There is just a single store with a single root reducing function
- Instead of adding stores, you split the root reducer into smaller reducers

## Reducer
Reducers in Redux are responsible for the state modifications that take place in response to actions. 
A reducer takes `state` and `action` as arguments, and it always returns a new `state`.

A reducer is a pure function with `(state, action) => state` signature

* `state` is read-only. In other words, the `reducer` function must always return a new copy of `state` and never modify state directly

### Combine Multiple Reducers
In order to let us combine multiple reducers together, Redux provides the combineReducers() method. This method accepts an object as an argument in which you define properties which associate keys to specific reducer functions. The name you give to the keys will be used by Redux as the name for the associated piece of state.

```javascript
const rootReducer = Redux.combineReducers({
  auth: authenticationReducer,
  notes: notesReducer
});
```

### States
The only way to mutate the internal state is to dispatch an action.

A state can be:
- a primitive
- an array
- an object
- an Immutable.js data structure

```javascript
function reducer(state = 0, action) {
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

## Actions
Actions provide instructions about what should change in the application `state` along with the necessary data to make those changes.
The actions can be serialized, logged or stored and later replayed.

```javascript
store.dispatch({ type: 'INCREMENT' }) // 1
store.dispatch({ type: 'INCREMENT' }) // 2
store.dispatch({ type: 'DECREMENT' }) // 1
```

### Action Creators
An action creator is simply a JavaScript function that returns an action. 
In other words, action creators create objects that represent action events.

```javascript
const action = {
  type: 'LOGIN'
}

function actionCreator() {
  return action;
}
```

## Store
Stores are used to hold the state of your app.

```javascript
let store = createStore(reducer)
```

Its API is:
- `store.subscribe()`
- `store.dispatch()`
- `store.getState()`


### Dispatch
`dispatch` method is what you use to dispatch actions to the Redux store. Calling `store.dispatch()` and passing the value returned from an action creator sends an action back to the store.

```javascript
// The following lines are equivalent, and both dispatch the action of type LOGIN
store.dispatch(actionCreator());
store.dispatch({ type: 'LOGIN' });
```

## Handle Asynchronous Actions

## React & Redux

### Provider
The `Provider` is a wrapper component that allows you to access the Redux `store` and `dispatch` functions throughout your component tree. 
`Provider` takes two props, the Redux store and the child components of your app. 

```jsx harmony
    <Provider store={store}>
      <App/>
    </Provider>
```

#### Map State and Dispatch to Props
The `Provider` component allows you to provide `state` and `dispatch` to your React components.
You must specify exactly what state and actions you want to make sure that each component only has access to the state it needs. 

You accomplish this by creating two functions:
- `mapStateToProps()`:  It should take `state` as an argument, then return an object which maps that state to specific property names.
- `mapDispatchToProps()`: It is used to provide specific action creators to your React components so they can **dispatch** actions against the Redux store.


````javascript
const mapStateToProps = (state) => { // state is passed as an argument
  return {
    messages: state
  }
};

const mapDispatchToProps = (dispatch) => { // dispatch is passed as an argument
  return {
    submitNewMessage: (message) => {
      dispatch(
          addMessage(message)
          );
    }
  }
};
````

### Connect Redux to React

The `connect` method takes two optional arguments, `mapStateToProps()` and `mapDispatchToProps()`.

To use this method, pass in the functions as arguments, and immediately call the result with your component.
````javascript
connect(
    mapStateToProps,
    mapDispatchToProps
    )(MyComponent)
````


### Useful Links and Notes

To remove something:
```javascript
    case 'REMOVE_ITEM':
        return {
            ...state,
            items: state.items.filter( item => item !== action.item )
        }
```