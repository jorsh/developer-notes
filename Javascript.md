# JavaScript

## Comments
//Comments
/*Multiple line comments*/

## Variable Data Types
	integer //all float 64 bits
	strings //use "" or '' but don't mix them
	boolean

## Conditional Code
	if(condition){}
		< > == !=

## Operators
### Aritmetic
    + - * /
### Assignment
    =
### Logical
    && (AND)
    || (OR)

### Modulus
    %
### Increment / Decrement
    ++
    --
### Ternary
    condition ? true : false

### Loops
    while(condition){}
    do{}while(condition);
    for(index;condition;increment){}
    break
    continue

### Functions
    function Name(Parameters){}

### Arrays[]
    methods()

### The Math Object
    Math.round();
    Math.max();

### String Properties
    string.lenght

### String Methods
    phrase.toUpperCase();
    prase.split(" ");
    prase.indexOf("word");  //Returns -1 if not
    prase.slice(start,lenght)

### Date
    Get Methods
        getMonth()
        getFullYear()
        getYear()
        getDate()
        getDay()
        getHours()
        getTime()
    Set Methods
        setDay()
    Comparing Dates

### Objects
    var = {property:value, property:value};

## JavaScript and the Browser

### Node Types

#### Element
Accessing DOM Nodes

Preferred:
- document.querySelector()
- document.querySelectorAll()
    
The Old Way:
- document.getElementByID("id");
- document.getElementsByClassName("class");
- document.getElementsByName("name");
- document.getElementsByTagName("tag");

Create - Append Child
- document.createElement("tag");
- element.appendChild(childNode);
- element.innerHTML("content")
- element.textContent("content")


#### Attribute
- getAttribute("attribute")
- setAttribute("attribute")

#### Text

### Events and Event Listeners
	
```javascript
// Capturing set to true by default. Bubbling if set to false
document.addEventListener('event',myFunction, true);
```

#### Common Events:
- onload
- onclick
- onmouseover
- onblur
- onfocus

https://developer.mozilla.org/en-US/docs/Web/Events


Timers
	setTimeout(function,miliseconds);
	setInterval(function,ms);

Styles
	Element.style.property = value; //in camelCase
	Element.className = class;

Coding Style
	Use camelCase for variables, functions and methods
	Case //Objects
	Open curly braces on the same line
	Always use blocks
	Define functions before you call them
	Always use var to define a variable
	//Search javascript style guideline

Minification Tools
	//
Quality Checker
	JSLint
	"use strict";

Regular Expressions
Javascript Prototypes


RESOURCES
https://developer.mozilla.org/en/JavaScript/Guide