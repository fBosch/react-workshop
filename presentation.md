class: center, middle

![React](https://upload.wikimedia.org/wikipedia/commons/thumb/a/a7/React-icon.svg/320px-React-icon.svg.png)
# Addition React Workshop

---

# Agenda

1. Introduction
2. Subjects
  * React Api
3. Open Discussion

---

# Introduction

---


# React API

The react API is designed similarly to the native APIs made for DOM manipulation that already exists on the modern web platforms.

Wit React you build the DOM using JavaScript instead of the alternative that most developers are familiar with — templating.

This allows React to render components much faster than most other competing frameworks — by using the virtual DOM diffing before rendering (similar to the way mergin with GIT works).
---

# [Example](/subjects/00-react-api/)

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
