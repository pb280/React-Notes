### Installing

`npm install react-router-dom`

<br>

<hr>

### While shifting to v6: Modify Old Changes

#### In `v5.1`

- Remove `<Redirect>` inside `<switch>`
- Refactor custom `<Route>`s

<br>

<hr>

## Major Steps for understanding `react-router-dom` library

#### Importing `BrowserRouter`

1. In `index.js`:

```
import { BrowserRouter } from react-router-dom;
```

2. Change root render function: Nest `<App />` inside `<BrowserRouter>`

Eg:

In `index.js 👇`

```
import React from 'react'
import ReactDOM from 'react-dom/client'
import { BrowserRouter } from 'react-router-dom'

import './index.scss'
import App from './App'
import reportWebVitals from './reportWebVitals'

const root = ReactDOM.createRoot(document.getElementById('root'))
root.render(
  <React.StrictMode>
    <BrowserRouter>
      <App />
    </BrowserRouter>
  </React.StrictMode>
)

// If you want to start measuring performance in your app, pass a function
// to log results (for example: reportWebVitals(console.log))
// or send to an analytics endpoint. Learn more: https://bit.ly/CRA-vitals
reportWebVitals()
```

<br>

#### Creating folder `routes` in "src" and adding components we need

<br>

#### Routing components & understanding routing pattern

For clear understanding refer API-Doc: https://reactrouter.com/en/main/start/tutorial#tutorial

<br>

In `App.js 👇`

```
import { Routes, Route, Outlet } from 'react-router-dom'

// @import Component: Home
import Home from './routes/home/home.component'

// Component: Navigation
const Navigation = () => {
  return (
    <div>
      <div>
        <h1>I am the navigation bar</h1>
      </div>
      <Outlet />
    </div>
  )
}

// Component: Shop
const Shop = () => {
  return <h1>I am shop page</h1>
}

// Main Component: App
const App = () => {
  return (
    <Routes>
      <Route path='/' element={<Navigation />}>
        <Route index element={<Home />} />
        <Route path='shop' element={<Shop />} />
      </Route>
    </Routes>
  )
}

export default App
```

<br>

🔑 Here, `<outlet />` denotes the children of the 'Navigation' component to be rendered.

> Eg: Children under of `<Route path='/' element={<Navigation />}>` who matching the route condition

<br>

🔑 Instead of anchor tags we use 'Link'

> `<Link className="demo" to="/shop">SHOP</Link>`
