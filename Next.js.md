# Next

- [Next](#next)
    - [Install](#install)
    - [Folder Structure](#folder-structure)
    - [Hello World](#hello-world)
    - [Styles](#styles)
    - [CSS in JS](#css-in-js)
    - [Adding metadata to **Head**](#adding-metadata-to-head)
    - [Fetching Data](#fetching-data)
    - [Routing](#routing)
    - [Dynamic Imports](#dynamic-imports)
    - [Custom Config](#custom-config)
    - [Static HTML Export](#static-html-export)
    - [Multi Zones](#multi-zones)
    - [Further Reading](#further-reading)

## Install

Just install next, react and react-dom.

```
npm install --save next react react-dom
```

Then configure the tasks it in `package.json`

```json
{
  "scripts": {
    "dev": "next",
    "build": "next build",
    "start": "next start"
  }
}
```

## Folder Structure

There are two main folders in a **Next** app:

- **pages**: It contains the pages that will be processed and rendered
- **static**: It contains the assets available to the app

## Hello World

Finally, create an `index.js` file in `/pages` folder

```javascript
export default () => <div>Hello World from Next.js!</div>;
```

## Styles

Next comes with **styled-jsx** to provide support for isolated scoped CSS.
https://www.npmjs.com/package/styled-jsx

But thes styles can be global.

```css
export default () =>
  <div>
    Hello world
    <p>scoped!</p>
    <style jsx>{`
      p {
        color: blue;
      }
      div {
        background: red;
      }
      @media (max-width: 600px) {
        div {
          background: gray;
        }
      }
    `}</style>
    <style global jsx>{`
      body {
        background: white;
      }
    `}</style>
  </div>
```

## CSS in JS

However Next also supports other methods to style components.
https://nextjs.org/docs/#css

Or simply inline styling:

```javascript
export default () => <p style={{ color: 'red' }}>hi there</p>;
```

## Adding metadata to **Head**

Very often we need to add metadata to the head of an HTML document. This is what the **Head** component allows us to do.

```javascript
import Head from 'next/head';

export default () => (
  <div>
    <Head>
      <title>My page title</title>
      <meta name="viewport" content="initial-scale=1.0, width=device-width" />
    </Head>
    <p>Hello world!</p>
  </div>
);
```

## Fetching Data

https://nextjs.org/docs/#fetching-data-and-component-lifecycle

Notice that to load data when the page loads, we use `getInitialProps` which is an async static method. It can asynchronously fetch anything that resolves to a JavaScript plain Object, which populates props.

```javascript
import React from 'react';
import 'isomorphic-unfetch';

export default class extends React.Component {
  static async getInitialProps() {
    const res = await fetch('https://jsonplaceholder.typicode.com/users/1');
    const json = await res.json();
    return { name: json.name };
  }

  render() {
    return <div>⭐️ {this.props.name}</div>;
  }
}
```

## Routing

Client-side transitions between routes can be enabled via a <Link> component

```javascript
// pages/index.js
import Link from 'next/link';

export default () => (
  <div>
    Click{' '}
    <Link href="/about">
      <a>here</a>
    </Link>{' '}
    to read more
  </div>
);
```

## Dynamic Imports

https://nextjs.org/docs/#dynamic-import

You can import JavaScript modules (inc. React Components) dynamically and work with them.
You can think dynamic imports as another way to split your code into manageable chunks.

There are four ways to do it. The following is the basic usage:

```javascript
import dynamic from 'next/dynamic';

const DynamicComponent = dynamic(import('../components/hello'));

export default () => (
  <div>
    <DynamicComponent />
    <p>HOME PAGE is here!</p>
  </div>
);
```

## Custom Config

For custom advanced behavior of Next.js, you can create a next.config.js in the root of your project director

_Note: next.config.js is a regular Node.js module, not a JSON file_

```javascript
// next.config.js
module.exports = {
  distDir: 'build',
};
```

You can even extend Webpack config on this file
https://nextjs.org/docs/#customizing-webpack-config

## Static HTML Export

https://nextjs.org/docs/#static-html-export

```javascript
// next.config.js
module.exports = {
  exportPathMap: function(defaultPathMap) {
    return {
      '/': { page: '/' },
      '/about': { page: '/about' },
      '/readme.md': { page: '/readme' },
      '/p/hello-nextjs': { page: '/post', query: { title: 'hello-nextjs' } },
      '/p/learn-nextjs': { page: '/post', query: { title: 'learn-nextjs' } },
      '/p/deploy-nextjs': { page: '/post', query: { title: 'deploy-nextjs' } },
    };
  },
};
```

and then run `next build && next export`

## Multi Zones

https://nextjs.org/docs/#multi-zones
https://github.com/zeit/micro-proxy

This is exactly the same concept as microservices, but for frontend apps.

```javascript
{
  "rules": [
    {"pathname": "/docs**", "method":["GET", "POST", "OPTIONS"], "dest": "https://docs.my-app.com"},
    {"pathname": "/**", "dest": "https://ui.my-app.com"}
  ]
}
```

## Further Reading

- https://nextjs.org/docs/#custom-%3Cdocument%3E
- https://nextjs.org/docs/#custom-error-handling
- https://github.com/zeit/next.js/tree/canary/examples
