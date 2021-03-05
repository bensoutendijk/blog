---
title: Tracking URL changes with React
description: Use React hooks to fire a callback whever the route changes for React Router
img: React.svg
tags: web dev, react, javascript
---
## Setup of URL change tracking
In this article, we'll show you how to use the built-in `useHistory` hook to track route changes in React Router.

You will want to have the BrowserRouter component wrapping your entire application like so

`index.jsx`
```jsx
import React from 'react' 
import ReactDOM from 'react-dom' 
import { BrowserRouter } from 'react-router-dom' 

import Root from './Root' 

ReactDOM.render( 
   <BrowserRouter> 
      <Root /> 
   </BrowserRouter>, 
   document.getElementById('root') 
)
```

### Listening for route changes
You can use hooks to listen for route changes

`Root.jsx`
```jsx
import React, { useEffect } from 'react' 
import App from './components/App' 

import { useHistory } from 'react-router-dom' const 

Root = () => { 
   const history = useHistory() 

   useEffect(() => {
      return history.listen((location) => { 
         console.log(`You changed the page to: ${location.pathname}`) 
      }) 
   },[history]) 

   return ( 
      <App /> 
   ) 
}
```

### Customizing the callback
Replace the `console.log` function with whatever you might need. For example, you can use this callback to fire a virtual pageview to your analytics software. Here's an example using [Mouseflow](https://mouseflow.com)

```jsx
useEffect(() => { 
   return history.listen((location) => { 
      window._mfq.push(['newPageView', location.pathname]); 
   }) 
}, [history])
```

And it is as simple as that. You can now add custom callbacks for all the route changes in your app.
