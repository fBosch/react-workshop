class: center, middle

![React](https://upload.wikimedia.org/wikipedia/commons/thumb/a/a7/React-icon.svg/320px-React-icon.svg.png)
# Addition React Workshop
``` bash
git clone https://github.com/fBosch/react-workshop.git
```
---

# Agenda

1. Rendering API

---

# Rendering API

With React you build the DOM using JavaScript objects (Virtual DOM) instead of the alternative that most developers are familiar with — templating.

By using the VDOM; React can find the difference of DOM trees (on application state change) before rendering and only re-render the changed nodes, similar to the way merging with GIT works.

This allows React to render components much faster than most other competing frameworks

![ReactDOM](https://3lhowb48prep40031529g5yj-wpengine.netdna-ssl.com/wp-content/uploads/2016/07/reactjs_component_rendering_performance_04.gif)

---

# Example: [ReactDOM](/subjects/00-rendering-api/)

The `ReactDOM` API is designed similarly to the native APIs made for DOM manipulation that already exist on the modern web platforms.

```js
// Vanilla
const rootElement = document.getElementById("root")

const element = document.createElement("div") // tagName
element.className = "component" // properties
element.appendChild(document.createTextNode("Hello!")) // children

rootElement.appendChild(element) // render
```

___
```js
// React
const rootElement = document.getElementById("root")

const element = React.createElement("div", { className: "component" }, "Hello!")
                              //   tagName        properties           children

ReactDOM.render(element, rootElement) // render
```
---

# JSX

It is possible to write a React application only by using the `React.createElement` API, but it can be hard on the eyes — so Facebook inventend an abstraction called JSX — which allows us to work with elements in a manner we're more used to: HTML.

It is not completely like HTML, it still relies on the same structures as the raw API — differences like the `className` property.

It needs to be transpiled using a process like Babel that will the JSX elements into `React.createElement` functions.

Summarized — JSX is highly recommended syntactic sugar.

---
class: center
# Typical Utilization

![Babel](https://www.adrianprieto.com/wp-content/uploads/2017/01/react-p.png)

---
# Example: [JSX](/subjects/01-jsx/)

```js
// Raw
const rootElement = document.getElementById("root")

const element = React.createElement("div", { className: "component" }, "Hello!")

ReactDOM.render(element, rootElement)
```
___
```js
// JSX
const rootElement = document.getElementById("root")

const element = <div className="component">Hello!</div>

ReactDOM.render(element, rootElement)
```
