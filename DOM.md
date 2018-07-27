# DOM

The DOM is the browser internal representation of a web page.

When the browser retrieves your HTML from your server, the parser analyzes the structure of your code, and creates a model of it.

## The Window Object
https://developer.mozilla.org/en-US/docs/Web/API/Window

The window object represents the window that contains the DOM document.


### properties

- console
- localStorage
- sessionStorage
- document
- history
- location

### methods
- addEventListener() / removeEventListener()
- setTimeout()
- setImmediate()
- alert()
- setInterval() / clearInterval()
- requestAnimationFrame()
- postMessage()


## The Document Object
https://developer.mozilla.org/en-US/docs/Web/API/Document

The document object represents the DOM tree loaded in a window.

### Properties
- document.title
- document.head
- document.body
- document.images
- document.links
- document.scripts
- document.styleSheetSets
- document.URL
- document.readyState

### Methods

- **document.querySelector()**
- **document.querySelectorAll()**
- document.getElementById()
- document.getElementsByClassName()
- document.getElementsByTagName()


### Traversing the DOM

 - Node.parentNode
 - Node.parentElement
- Node.childNodes
- Node.firstElementChild
- Node.lastElementChild
- Node.previousElementSibling
- Node.nextElementSibling


### Editing the DOM

- document.createElement()
- document.createTextNode()
- document.appendChild()
- first.removeChild(second)
- document.insertBefore(newNode, existingNode)
- element.appendChild(newChild)
- element.prepend(newChild)
- element.replaceChild(existingChild, newChild)
- element.insertAdjacentElement(position, newElement)
- element.textContent = 'something'