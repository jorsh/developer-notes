- [React](#react)
  - [Hello World](#hello-world)
  - [JSX](#jsx)
  - [Elements](#elements)
  - [Components](#components)
    - [Functional Components](#functional-components)
      - [9 Benefits of Stateless Functional Components](#9-benefits-of-stateless-functional-components)
    - [Class Components](#class-components)
    - [Props are Read-Only](#props-are-read-only)
    - [propTypes](#proptypes)
      - [Custom propType validation](#custom-proptype-validation)
    - [defaultProps](#defaultprops)
    - [Access nested data with props.children](#access-nested-data-with-propschildren)
    - [Rendering a Component](#rendering-a-component)
    - [Composition and Extraction](#composition-and-extraction)
    - [Container vs Presentation Components](#container-vs-presentation-components)
    - [Other APIs](#other-apis)
    - [Class Properties](#class-properties)
    - [Instance Properties](#instance-properties)
  - [State](#state)
    - [Adding Local State to a Class](#adding-local-state-to-a-class)
    - [Seting State](#seting-state)
      - [Do Not Modify State Directly](#do-not-modify-state-directly)
      - [State Updates May Be Asynchronous](#state-updates-may-be-asynchronous)
      - [State Updates are Merged](#state-updates-are-merged)
  - [Lifecycle](#lifecycle)
    - [Mounting](#mounting)
    - [Updating](#updating)
    - [Unmounting](#unmounting)
  - [Handling Events](#handling-events)
  - [Conditional Rendering](#conditional-rendering)
    - [Inline if with logical && operator](#inline-if-with-logical--operator)
    - [Inline if-else with ternary operator](#inline-if-else-with-ternary-operator)
    - [Preventing from rendering](#preventing-from-rendering)
  - [Lists and Keys](#lists-and-keys)
    - [Keys](#keys)
  - [Forms](#forms)
  - [React Top-Level API](#react-top-level-api)
  - [React Router](#react-router)
    - [Basic](#basic)
    - [Nesting](#nesting)
    - [URL params](#url-params)
    - [Link](#link)
    - [Other config](#other-config)
  - [Axios](#axios)
  - [Questions](#questions)
  - [Resources](#resources)


# React
## Hello World
```javascript
import React from 'react';
import ReactDOM from 'react-dom';

ReactDOM.render(
  <h1>Hello, world!</h1>,
  document.getElementById('root')
);
```

## JSX
- It is a syntax extension to JavaScript
- Use it to describe what the UI should look like
- JSX produces React "elements"
- You can embed any JavaScript expression in JSX by wrapping it in curly braces

```javascript
const element = (
  <h1>
    Hello, {formatName(user)}!
  </h1>
);
```
- Use quotes to specify string literals as attributes: `const element = <div tabIndex="0"></div>;`
- Use curly braces to embed a JavaScript expression in an attribute: `const element = <img src={user.avatarUrl}></img>`
- If a tag is empty, you may close it immediately with />

## Elements
- Elements are the smallest building blocks of React apps
- An element describes what you want to see on the screen: `const element = <h1>Hello, world</h1>;`
- Elements are what components are "made of"
- React elements are immutable
- An element is like a single frame in a movie: it represents the UI at a certain point 

## Components
- Components let you split the UI into independent, reusable pieces
- Conceptually, components are like JavaScript functions
- They accept arbitrary inputs (called "props") and return React elements describing what should appear on the screen

### Functional Components
They are called "functional" components because they are literally JavaScript functions.
````javascript
function Welcome(props) {
  return <h1>Hello, {props.name}</h1>;
}
````

#### 9 Benefits of Stateless Functional Components
- No class needed
- Avoid 'this' keyword
- Enforced best practices
- High signal-to-noise ratio
- Enhanced code completion / intellisense
- Bloated components are obvious
- Easy to understand
- Easy to test
- Performance

### Class Components

```javascript
class Welcome extends React.Component {
  render() {
    return <h1>Hello, {this.props.name}</h1>;
  }
}
```
The above two components are equivalent from React's point of view.

| Class Components  | Stateless Components |
| ----------------- | -------------------- |
| State             | Everywhere else      |
| Refs              |                      |
| Lifecycle methods |                      |
| Child functions   |                      |

### Props are Read-Only
Props are useful for passing data from one component to another child component. props are to components what arguments are to functions.

- Whether you declare a component as a function or a class, it must never modify its own props
- **All React components must act like pure functions with respect to their props**

**Pure Functions**: they do not attempt to change their inputs, and always return the same result for the same inputs

### propTypes
These can be used to make sure the data you receive is valid. When an invalid value is provided for a prop, a warning will be shown in the JavaScript console.
```jsx harmony
class Greeting extends React.Component {}

Greeting.propTypes = {
  name: React.PropTypes.string
};
```

#### Custom propType validation
You can use custom validation to display different messages depending on the invalid prop.
````jsx harmony
    Greeting.propTypes = {
      name(props, propName, component){
        if(!(propName in props)){
          return new Error(`missing ${propName}`)
        }
        if(props[propName].length < 6){
          return new Error(`${propName} was too short`)
        }
      }
    }
````


### defaultProps
```jsx harmony
Greeting.defaultProps = {
  name: 'Mary'
};
```

### Access nested data with props.children
It is a way to gain access to whatever is between the opening and closing tags.
```jsx harmony
function App() {
  return <Button>React</Button>
}

function Button(props) {
  return <button>{props.children}</button>
}
```
**In the example above the result will be a button labeled 'React'.**

### Rendering a Component
Elements can also represent user-defined components:
`const element = <Welcome name="Sara" />;`
- Always start component names with a capital letter

When React sees an element representing a user-defined component, it passes JSX attributes to this component as a single object (props).
```javascript
function Welcome(props) {
  return <h1>Hello, {props.name}</h1>;
}

const element = <Welcome name="Sara" />;
ReactDOM.render(
  element,
  document.getElementById('root')
);

// Output: Hello Sara
```

### Composition and Extraction
- Components can refer to other components in their output
- Components must return a single root element
- If a part of your UI is used several times (Button, Panel, Avatar), or is complex enough on its own (App, FeedStory, Comment), it is a good candidate to be a reusable component
- **The data flows down**: This is commonly called a "top-down" or "unidirectional" data flow

```javascript
function Comment(props) {
  return (
    <div className="Comment">
      <UserInfo user={props.author} />
    </div>
  );
}
```

### Container vs Presentation Components

- Container components, aka: Smart, Stateful, Controller view
- Presentational, aka: Dumb, Stateless, View

| Container                  | Presentation                       |
| -------------------------- | ---------------------------------- |
| Little to no markup        | Nearly all markup                  |
| Pass data and actions down | Receive data and actions via props |
| Knows about Redux          | Doesn't know about Redux           |
| Often stateful             | Typical functional components      |


### Other APIs
- `setState()`
- `forceUpdate()`

### Class Properties
- `defaultProps`
- `displayName`
- `propTypes`

### Instance Properties
- `props`
- `state`


## State
State is similar to props, but it is private and fully controlled by the component.
It is a state if:
- Is it passed in by a parent via props
- Does it change over time?
- Can you compute it?

### Adding Local State to a Class
```javascript
class Clock extends React.Component {
  constructor(props) {
    super(props);
    this.state = {date: new Date()};
  }
  render(){
      return (
        <h2>It is {this.state.date.toLocaleTimeString()}.</h2>
      )
  } 
}
```
*Class components should always call the base constructor with `props`.*

### Seting State
- The `setState()` method allows you to update the current state. 
- By using `setState()` React knows that the state has changed, and calls `render()` method again (Unless `shouldComponentUpdate()` returns `false`)

#### Do Not Modify State Directly
```javascript
// Wrong
this.state.comment = 'Hello';

// Correct
this.setState({comment: 'Hello'});
```
*The only place where you can assign `this.state` is the constructor.*

#### State Updates May Be Asynchronous
To fix it, use a second form of `setState()` that accepts a function rather than an object
```javascript
this.setState((prevState, props) => ({
  counter: prevState.counter + props.increment
}));
```

#### State Updates are Merged
You can update them independently with separate setState() calls:

```jsx harmony
componentDidMount(){
      this.setState({
        posts: response.posts
      });
      
      this.setState({
        comments: response.comments
      });
  }
```
*`this.setState({comments})` leaves `this.state.posts` intact, but completely replaces `this.state.comments`*
## Lifecycle
- Each component has several "lifecycle methods" that you can override to run code at particular times in the process
- Methods prefixed with will are called **right before** something happens
- Methods prefixed with did are called **right after** something happens.

### Mounting
These methods are called when an instance of a component is being created and inserted into the DOM:
- `constructor()`
- `componentWillMount()`
- `render()`
- `componentDidMount()`

### Updating
An update can be caused by changes to `props` or `state`.

These methods are called when a component is being re-rendered:
- `componentWillReceiveProps()`
- `shouldComponentUpdate()`
- `componentWillUpdate()`
- `render()`
- `componentDidUpdate()`

### Unmounting
This method is called when a component is being removed from the DOM:
- `componentWillUnmount()`


## Handling Events
- React events are named using camelCase, rather than lowercase.
- With JSX you pass a function as the event handler, rather than a string.
````html
<!--DOM Elements-->
<button onclick="activateLasers()">
  Activate Lasers
</button>

<!--React Elements-->
<button onClick={activateLasers}>
  Activate Lasers
</button>
````

 If you forget to bind this.handleClick and pass it to onClick, this will be undefined when the function is actually called.

```javascript
class Toggle extends React.Component {
  constructor(props) {
    super(props);
    
    // This binding is necessary to make `this` work in the callback
    this.handleClick = this.handleClick.bind(this);
  }
  }
```

## Conditional Rendering
- In React, you can render only some components depending on the state of your application.
- Conditional rendering in React works the same way conditions work in JavaScript, by using `if` or the ternary operator.
````jsx harmony
render() {
    const isLoggedIn = this.state.isLoggedIn;

    let button = null;
    if (isLoggedIn) {
      button = <LogoutButton onClick={this.handleLogoutClick} />;
    } else {
      button = <LoginButton onClick={this.handleLoginClick} />;
    }

    return (
      <div>
        <Greeting isLoggedIn={isLoggedIn} />
        {button}
      </div>
    );
  }
````

### Inline if with logical && operator
- You may embed any expressions in JSX by wrapping them in curly braces.
- `true && expression` always evaluates to `expression`
- `false && expression` always evaluates to `false`
 
````jsx harmony
function Mailbox(props) {
  const unreadMessages = props.unreadMessages;
  return (
    <div>
      <h1>Hello!</h1>
      {unreadMessages.length > 0 &&
        <h2>
          You have {unreadMessages.length} unread messages.
        </h2>
      }
    </div>
  );
}
````

### Inline if-else with ternary operator
````jsx harmony
render() {
  const isLoggedIn = this.state.isLoggedIn;
  return (
    <div>
      The user is <b>{isLoggedIn ? 'currently' : 'not'}</b> logged in.
    </div>
  );
}
````
### Preventing from rendering
- In rare cases you might want a component to hide itself even though it was rendered by another component. 
- To do this return null instead of its render output.
````jsx harmony
function WarningBanner(props) {
  if (!props.warn) {
    return null;
  }

  return (
    <div className="warning">
      Warning!
    </div>
  );
}

// and in render
<WarningBanner warn={this.state.showWarning} />
````

## Lists and Keys
````jsx harmony
const numbers = [1, 2, 3, 4, 5];
const listItems = numbers.map((number) =>
  <li>{number}</li>
);

// And in render
ReactDOM.render(
  <ul>{listItems}</ul>,
  document.getElementById('root')
);
````

### Keys
- Keys help React identify which items have changed, are added, or are removed
- Keys should be given to the elements inside the array to give the elements a stable identity
- Most often you would use IDs from your data as keys
- You may use the item index as a key as a last resort `todos.map((todo, index)=>{}`
- A good rule of thumb is that elements inside the map() call need keys
- Keys used within arrays should be unique among their siblings. They don't need to be globally unique


````jsx harmony
const numbers = [1, 2, 3, 4, 5];
const listItems = numbers.map((number) =>
  <li key={number.toString()}>
    {number}
  </li>
);
````

## Forms

HTML form elements work a little bit differently from other DOM elements in React, because form elements naturally keep some internal state.


## React Top-Level API

## React Router



### Basic
````jsx harmony
import { render } from 'react-dom'
import { Router, Route, browserHistory } from 'react-router'

// Import RootView and NoMatch

render((
  <Router history={browserHistory}>
    <Route path="/" component={RootView} />
    <Route path="*" component={PageNotFound} />
  </Router>
), document.getElementById('app'))
````

### Nesting
````jsx harmony
import React from 'react'
import { render } from 'react-dom'
import { Router, Route, browserHistory } from 'react-router'

// Import About, Inbox and Messages

class Chrome extends React {
  render () {
    return (
      <div>
        <h1>App</h1>
        <a href="/about">About</a>
        <a href="/inbox">Inbox</a>
        <a href="/messages">Messages</a>
        { this.props.children }
      </div>
    )
  }
}

render((
  <Router history={browserHistory}>
    <Route path="/" component={Chrome}>
      <Route path="about" component={About} />
      <Route path="inbox" component={Inbox} />
      <Route path="messages" component={Messages} />
    </Route>
  </Router>
), document.getElementById('app'))
````

### URL params
````jsx harmony
class Message extends React {
  componentDidMount() {
    // from the path `/inbox/messages/:id`
    const id = this.props.params.id
    ...
````

### Link
````jsx harmony
import { Link } from 'react-router'

/* Nav Component */
  ...
  render() {
    ...
    const userId = 10;

    return (
      // Adding params is as simple as appending them to the route
      <Link to={`user/${userId}`}>User 10</Link>

      // Classes can be added to the link element if the current route is the one they link to
      <Link to="login"
        activeClassName="-active">Login</Link>
    )
  }
````

### Other config
````jsx harmony
<Route path="/">
  <IndexRoute component={Home} />  //to specify the default page
  <Route path="*" handler={NotFound} />

  // arbitrary/url/login -> /arbitrary/url/sessions/new
  <Redirect from="login" to="sessions/new" />
  // arbitrary/url/about/1 -> /arbitrary/url/profile/1
  <Redirect from="about/:id" to="profile/:id" />

  <Route name="about-user" ... />
  ...
````


## Axios

## Questions
- What is React?
- What is an element?
- Why elements are immutable?
    - A: Once you create an element, you can't change its children or attributes
- What is a component?
- What is the difference between functional components and class components?

- What is a stateful and what is a stateless component?
- Are function components and stateless functional components the same thing?
- Can a parent or child component know if certain component is stateful or stateless?
- How components communicate?
- What is the difference between an Element and a Component?
- What is JSX?
- What does JSX mean?
- Is it possible to replace JSX with another language/library?
    - A: Plain javascript can be used
- Is it possible to use css and html urls on react components?

- Is it possible for a component to have access to the state of other components? 
- What is the difference between props and state?
- When to declare something as state and when is a prop?
    - If you don't use something in render(), it shouldn't be in the state.
- Why can't we just use `this.state.comment = 'Hello'` instead of `setState()`  
- Why is React's concept of Virtual DOM said to be more performant than dirty model checking?
- What are some good practices to style components?
- Why use Redux over Flux?
- Does render method get called any time “setState” is called?


## Resources
- https://github.com/reactjs/react-router-tutorial/tree/master/lessons
- https://freecodecamp.github.io/wiki/en/react-router-cheatsheet/
