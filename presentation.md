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

Wit React you build the DOM using JavaScript objects (Virtual DOM) instead of the alternative that most developers are familiar with — templating.

By using the VDOM; React can find the difference of DOM trees (on application state change) before rendering and only re-render the changed nodes, similar to the way merging with GIT works.

This allows React to render components much faster than most other competing frameworks

---

# Example: [ReactDOM](/subjects/00-rendering-api/)

The ReactDOM API is designed similarly to the native APIs made for DOM manipulation that already exist on the modern web platforms.

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
