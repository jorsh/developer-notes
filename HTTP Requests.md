# HTTP Requests

## XMLHttpRequest (XHR)

The following code creates an XMLHttpRequest (XHR) request object, and attaches a callback function that responds on the onreadystatechange event.

The xhr connection is set up to perform a GET request to https://file.json, and it’s started with the send() method:



```javascript
const xhr = new XMLHttpRequest()
xhr.onreadystatechange = () => {
  if (xhr.readyState === 4) {
    xhr.status === 200 ? console.log(xhr.responseText) : console.error('error')
  }
}
xhr.open('GET', 'https://file.json')
xhr.send()
```

Other parameters let you specify a flag to make the request synchronous if set to false, and a set of credentials for HTTP authentication:
```javascript
open(method, url, asynchronous, username, password)
```

### onreadystatechange
The onreadystatechange is called multiple times during an XHR request. We explicitly ignore all the states other than readyState === 4, which means the request is done.

The states are
- 1 (OPENED): the request starts
- 2 (HEADERS_RECEIVED): the HTTP headers have been received
- 3 (LOADING): the response begins to download
- 4 (DONE): the response has been downloaded


### Aborting an XHR Request
An XHR request can be aborted by calling the abort() method on the xhr object.

```javascript
if (OH_NOES_WE_NEED_TO_CANCEL_RIGHT_NOW_OR_ELSE) {
  xhr.abort();
}
```

## Fetch
https://developer.mozilla.org/en-US/docs/Web/API/WindowOrWorkerGlobalScope/fetch

The Fetch API provides a JavaScript interface for accessing and manipulating parts of the HTTP pipeline, such as requests and responses. It also provides a global fetch() method that provides an easy, logical way to fetch resources asynchronously across the network.

```javascript
fetch('./file.json')
  .then(response => response.json()) //or response.text()
  .then(data => console.log(data))
```

### Catching Errors

```javascript
fetch('./file.json')
.then(response => {
  //...
}
.catch(err => console.error(err))
```


### Request Object
The Request object represents a resource request, and it’s usually created using the new Request() API.

The Request object offers several read-only properties to inspect the resource request details, including

- method: the request’s method (GET, POST, etc.)
- url: the URL of the request.
- headers: the associated Headers object of the request
- referrer: the referrer of the request
- cache: the cache mode of the request (e.g., default, reload, no-cache).
And exposes several methods including json(), text() and formData() to process the body of the request.

```javascript
const request = new Request('./file.json', {
  headers: new Headers({
    'Content-Type': 'application/json'
  })
})
fetch(request)
```

### Aborting a fetch request
```javascript
const controller = new AbortController()
const signal = controller.signal

fetch('./file.json', { signal })

// You can set a timeout that fires an abort event 5 seconds after the fetch request has started, to cancel it:
setTimeout(() => controller.abort(), 5 * 1000)
```

- Polyfill
https://github.com/github/fetch


```javascript

```
