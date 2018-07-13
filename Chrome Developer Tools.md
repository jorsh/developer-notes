# Chrome Developer Tools
### Opening the tools

## Console
Use the Console to log diagnostic information during development or use it as a shell to interact with the JavaScript on the page.

#### Shortcuts
- Open the Console Panel
    - `Press Ctrl+Shift+J (Windows / Linux) or Cmd+Opt+J (Mac)`
- Console Drawer (while in Dev Tools)
    - `esc`

#### Capabilities
- Unstack the output: Go to settings and uncheck TimeStamps
- Right Click and Save to save the console output


### Diagnose and Log
- Use `console.log()` or `console.debug()` for basic logging
- Use `console.info()` for basic logging with an info icon next to the output
- Use `console.error()` for eye-catching stuff
- Use `console.warn()` to display a yellow warning icon with the message text
- Use `console.group()` and `console.groupEnd()` to group related messages. It can be nested.
    - Alt `.console.groupCollapsed()` is the same as `console.group()` but collapsed initially
- Use `console.assert()` to show conditional error messages
    - e.g. `console.assert(list.childNodes.length < 500, "Node count is > 500");`
- Use `console.dir()` to format DOM elements as JavaScript objects
- Use `console.table()` to format data as a Table
    - e.g. `console.table([[1,2,3], [2,3,4]]);`
- Use `window.onerror` to handle errors happening during execution


### Measure execution times
- Use `console.time()` and `console.timeEnd()` to track time elapsed between code execution points
- Use `console.count(label)` to count how many times the same string is passed to a function
- Use `console.timeStamp()` to add a mark to the timeline from the console (Timeline Panel should be opened)
- Use `console.trace()` to print a stack trace from the point where the method was called




### String substitution and formatting

|Specifier | Output|
| :-----: | :---- |
|%s|	Formats the value as a string|
|%i or %d|	Formats the value as an integer|
|%f|	Formats the value as a floating point value|
|%o|	Formats the value as an expandable DOM element. As seen in the Elements panel|
|%O|	Formats the value as an expandable JavaScript object|
|%c|	Applies CSS style rules to the output string as specified by the second parameter|


### Styling console output with CSS
```
console.log("%cThis will be formatted with large, blue text", "color: blue; font-size: x-large");
```

### Select elements
|Shortcut|Description|
|:---:|---|
|`$(selector)`|	Returns the first element that matches the specified CSS selector. Shortcut for document.querySelector().|
|`$$(selector)`|	Returns an array of all the elements that match the specified CSS selector. Alias for document.querySelectorAll().|
|`$x(path)`|	Returns an array of elements that match the specified XPath.|

### Monitor Events
- Use the `monitorEvents()` to log information on the specified targets
    - `monitorEvents(document.body, "click");`   
- Use `unmonitorEvents()` to stop listening
- Get listeners of a DOM element using `getEventListeners()`
- Use the Event Listeners Inspector panel to get information on event listeners

| Event type | Corresponding mapped events |
|-----------|-----------------------------|
| mouse | "mousedown", "mouseup", "click", "dblclick", "mousemove", "mouseover", "mouseout", "mousewheel" |
| key |	"keydown", "keyup", "keypress", "textInput" |
| touch | "touchstart", "touchmove", "touchend", "touchcancel" |
| control |	"resize", "scroll", "zoom", "focus", "blur", "select", "change", "submit", "reset" |
    

### CLI Reference
- `$_` returns the value of the most recently evaluated expression
- `$0` ... `$4` work as a historical reference to the last five DOM elements inspected within the Elements panel
- Use `clear()` or `Ctrl + L` to clear the console
- Use `copy(object)` to copy a string representation of the specified object to the clipboard
- `keys(object)` returns an array containing the names of the properties belonging to the specified object
- `monitor(function)` logs a message when the function is called
- `unmonitor(function)` stops the monitoring of the specified function
- Use `debug(getData)` to invoke the debugger when the specified function is called, 
- Use `undebug(fn)` to stop breaking on the function, or use the UI to disable all breakpoints
- `dir(object)` displays an object-style listing of all the specified object's properties
- `dirxml(object)` prints an XML representation of the specified object
- `inspect(object/function)` opens and selects the specified element or object in the appropriate panel
- `profile()` starts a JavaScript CPU profiling session with an optional name
- `profileEnd()` completes the profile and displays the results in the Profile panel
- Use `table(data[, columns])` to log object data with table formatting by passing in a data object in with optional column headings
- `values(object)` returns an array containing the values of all properties belonging to the specified object


## Elements

## Sources
## Network
## Timeline
## Profiles
## Application
## Security