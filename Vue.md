# Vue

Vue is a progressive framework for building user interfaces.
The core library is focused on the view layer only.



## Declarative Rendering

```
// index.html
<div id="app">
  {{ message }}
</div>


// script.js
var app = new Vue({
  el: '#app',
  data: {
    message: 'Hello Vue!'
  }
})
```



## Directives
Directives are prefixed with v- to indicate that they are special attributes provided by Vue.
They apply special reactive behavior to the rendered DOM.


## Conditionals and Loops

### v-if
```
// .html
<div id="app-3">
  <span v-if="seen">Now you see me</span>
</div>


// .js 
var app = new Vue({
  el: '#app-3',
  data: {
    seen: true
  }
})
```

### v-for
v-for directive can be used for displaying a list of items using the data from an Array:

```
<ol>
  <li v-for="number in numbers">
    {{ number }}
  </li>
</ol>

var app = new Vue({
  ...
  data: {
    numbers: [ 2, 3, 4, 5]
  }
})
```


## Handling User Input

To let users interact with your app, we can use the v-on directive to attach event listeners that invoke methods on our Vue instances:

```
<button v-on:click="logMessage">Log Message</button>


 var app = new Vue({
  ...
  methods: {
    logMessage: function () {
      console.log('Button Clicked')
    }
  }
})
```


### v-model
Vue also provides the v-model directive that makes two-way binding between form input and app state a breeze:

```
<p>{{ message }}</p>
<input v-model="message">


var app = new Vue({
  ...
  data: {
    message: 'Hello Vue!'
  }
})
```

## Composing with Components

In Vue, a component is essentially a Vue instance with pre-defined options. Registering a component in Vue is straightforward:

```
// Define a new component called todo-item
Vue.component('todo-item', {
  template: '<li>This is a todo</li>'
})
```