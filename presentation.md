class: center, middle, dark-background
background-image: url(https://alisd.io/assets/lazy_react_background.png)

# React Workshop
``` bash
git clone https://github.com/fBosch/react-workshop.git
```
---

# Agenda

1. Rendering API
2. JSX
3. Components

---

# Rendering API

With React you build the DOM using JavaScript objects (Virtual DOM) instead of the alternative that most developers are familiar with — templating.

By using the VDOM; React can find the difference of DOM trees (on application state change) before rendering and only re-render the changed nodes, similar to the way merging with GIT works.

This allows React to render components much faster than most other competing frameworks

![ReactDOM](https://3lhowb48prep40031529g5yj-wpengine.netdna-ssl.com/wp-content/uploads/2016/07/reactjs_component_rendering_performance_04.gif)

---

# [ReactDOM](/subjects/00-react-dom/)

The React API is worded similarly to the native APIs made for DOM manipulation that already exist on the modern web platforms.

```js
// 🍦Vanilla
const rootElement = document.getElementById("root")

const element = document.createElement("div") // tagName
element.className = "container" // properties
element.appendChild(document.createTextNode("Hello!")) // children

rootElement.appendChild(element) // render
```

___
```js
// ⚛️React
const rootElement = document.getElementById("root")

const element = React.createElement("div", { className: "container" }, "Hello!")
                              //   tagName        properties           children

ReactDOM.render(element, rootElement) // render
```
---

# JSX

It is possible to write a React application only by using the `React.createElement` API, but it can be hard to maintain — so Facebook invented an abstraction layer called JSX, which allows us to work with elements in a manner that we're more accustomed to: HTML.

It is not completely like HTML, it still relies on the same data structures as the raw API — for example; differences like the `className` property instead of using `class`.

JSX needs to be transpiled to regular JavaScript using a transpiler, like Babel, that will turn the JSX element declarations into `React.createElement` function calls.

Summarized — JSX is **highly** recommended syntactic sugar when building a React application

---
class: center
# Typical Utilization

![Babel](https://www.adrianprieto.com/wp-content/uploads/2017/01/react-p.png)

---
# [JSX Transpilation](/subjects/01-jsx/)

Here you can see the abstraction in action — which, arguably, results in much more readable code.

```jsx
// JSX
const element = <div className="container">Hello!</div>

```
___

```js
// Transpiled 🔀
const element = React.createElement("div", { className: "container" }, "Hello!")

```
---
# Components

In React, components are simply functions that return a react element (JSX). Components must be pure — which means that they must not modify the `props` that they are passed or rely on external state that is not passed through `props`.

There is two ways to write a React component:

🤖 Dumb Components

  — are simple functions that take input (`props`) and returns JSX. They are stateless, primarily presentational and are often used as small UI parts that are composed together in smart components.
___
🧠 Smart Components

  — are, typically, class based functions that contain application state and can trigger re-render upon state change. These are commonly where you would make fetch requests and other logic that is not view specific.

---

# [🤖 Dumb Component](/subjects/02-components/dumb.html)

```jsx
// Dumb component utilized with interpolation (curly braces within JSX)
const greeting = props => <div className="container">{props.content}</div>
const element = (
  <div className="app">
    {greeting({ content: "Hello from component"})}
  </div>
)
```
___

```jsx
// Better way — using JSX by following recommended conventions
const Greeting = props => <div className="container">{props.content}</div>
const element = (
  <div className="app">
    <Greeting content="Hello from component" />
  </div>
)
```
Using CamelCased naming for your component functions allows the JSX transpiler to know that it is referencing a variable  — otherwise it will try to interpretate it as a `tagName` string.

---

# [🧠 Smart Component](/subjects/02-components/smart.html)

Smart components are typically based on the the react Component class, which implements a number of useful lifecycle hooks and methods.

The render method is run every time a passed `prop` or internal `state` is changed.

A re-render will not be triggered upon mutation — React does not use two-way databinding.

```jsx
class Counter extends React.Component {
  state = { count: 0 }
  // methods that alter state without mutation — triggering a component re-render
  increment = () => this.setState({ count: this.state.count + 1 })
  decrement = () => this.setState({ count: this.state.count - 1 })

  render() {
    return (
      <div className="counter">
        {this.state.count}
        <button onClick={this.increment}>+</button>
        <button onClick={this.decrement}>-</button>
      </div>
    )
  }
}
```
