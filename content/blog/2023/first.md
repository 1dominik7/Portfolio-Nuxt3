---
description: A beginner's guide to getting started with Vue 3.
image: /images/vue-logo.png
head:
  meta:
    - name: "og:image"
      content: /images/vue-logo.png
publishedAt: 2023-05-12 15:20:00
toc: true
---

# Introduction to React

![Vue 3 Introduction](/images/react-logo.png)

## What is React?

React is a JavaScript library created by Facebook. React is a User Interface (UI) library. React is a tool for building UI components

---

## Why Choose React?

Let's explore six key reasons to use React.js:

- **React is Flexible:** React is remarkably flexible. Once you have learned it, you can use it on a vast variety of platforms to build quality user interfaces. React is a library, NOT a framework. Its library approach has allowed React to evolve into such a remarkable tool.

React was created with a single focus: to create components for web applications. A React component can be anything in your web application like a Button, Text, Label, or Grid.

But as React's popularity is grown, its ecosystem has also grown to cover various use cases.

You can generate a static site with React using tools like Gatsby. You can use React Native to build mobile apps. You can even create Desktop applications using a tool like Electron, which can run on mac and windows with React.js technology.

- **React Has a Great Developer Experience:** Your team will fall in love with React when they start coding in it. Rapid development and React's small API combined creates a fantastic developer experience.

React's API is very simple to learn. It has very few concepts to learn. Here is a small example of a React Component:

```javascript
import React from "react";

function Message(props) {
  return <div>Hello {props.name}</div>;
}
```

You just need to import the React library. Message is the component that accepts props (input) and returns JSX.

JSX is a special syntax that looks like HTML, which converts React's API calls and finally renders HTML.

Traditional frameworks like Angular and Vue power up the HTML. They use JavaScript inside HTML. They have created HTML attributes that give extra capabilities to it.

The main problem with this approach is that you have to learn those new HTML attributes or always keep looking at the official documentation.

- **React Has Facebook's Support/Resources:** React is heavily used in the Facebook app, website, and in Instagram. That's why Facebook is deeply committed to it. They use over 50k React components in their production environment. The top four React contributors on GitHub are full-time Facebook employees.

- **React Has Broader Community Support, Too:** Since 2015, React's popularity has grown steadily. It has a massive active community and its GitHub Repository has over 164k Stars. It is one of the Top 5 Repositories on GitHub. Reactiflux is a community specially made for React Developers. Over 110k community members are involved in helping solve and share React-related problems.

One of the most popular websites among software developers is StackOverflow. You can see that there are over 250k questions asked about React and related libraries.

- **React Has Great Performance:** The React team realized that JavaScript is fast, but updating the DOM makes it slow. React minimizes DOM changes. And it has figured out the most efficient and intelligent way to update DOM.

Before React, most frameworks and libraries would update the DOM unintelligently to reflect a new state. This resulted in changes to a significant portion of the page.

React monitors the values of each component's state with the Virtual DOM. When a component's state changes, React compares the existing DOM state with what the new DOM should look like. After that, it finds the least expensive way to update the DOM.

This doesn't seem very easy, but React handles it very well behind the scenes. It has multiple benefits like avoiding layout trashing, which is when the browser has to re-calculate the position of everything when the DOM element changes.

- **React is Easy to Test:** React's design is very user friendly for testing.

  Traditional UI browser testing is a hassle to setup. On the other hand, you require very little or no configuration for testing in React.
  Traditional UI browser requires browsers for testing, but you can test React components quickly and easily using the node command-line.
  Traditional UI browser testing is slow. But command-line testing is fast, and you can run a considerable amount of test suites at a time.
  Traditional UI browser testing is often time consuming and challenging to maintain. React test can be written quickly using tools like Jest & Enzyme.

---

## Getting Started with React

In React, a component is a reusable module that renders a part of our overall application. Components can be big or small, but they are usually clearly defined: they serve a single, obvious purpose.

Let's open src/App.jsx, since our browser is prompting us to edit it. This file contains our first component, <App />:

```javascript
import { useState } from "react";
import reactLogo from "./assets/react.svg";
import viteLogo from "/vite.svg";
import "./App.css";

function App() {
  const [count, setCount] = useState(0);

  return (
    <>
      <div>
        <a href="https://vitejs.dev" target="_blank">
          <img src={viteLogo} className="logo" alt="Vite logo" />
        </a>
        <a href="https://react.dev" target="_blank">
          <img src={reactLogo} className="logo react" alt="React logo" />
        </a>
      </div>
      <h1>Vite + React</h1>
      <div className="card">
        <button onClick={() => setCount((count) => count + 1)}>
          count is {count}
        </button>
        <p>
          Edit <code>src/App.jsx</code> and save to test HMR
        </p>
      </div>
      <p className="read-the-docs">
        Click on the Vite and React logos to learn more
      </p>
    </>
  );
}

export default App;
```

The App.jsx file consists of three main parts: some import statements at the top, the App() function in the middle, and an export statement at the bottom. Most React components follow this pattern.
Import statements

The import statements at the top of the file allow App.jsx to use code that has been defined elsewhere. Let's look at these statements more closely.

```javascript
import { useState } from "react";
import reactLogo from "./assets/react.svg";
import viteLogo from "/vite.svg";
import "./App.css";
```

The first statement imports the useState hook from the react library. Hooks are a way of using React's features inside a component. We'll talk more about hooks later in this tutorial.

After that, we import reactLogo and viteLogo. Note that their import paths start with ./ and / respectively and that they end with the .svg extension at the end. This tells us that these imports are local, referencing our own files rather than npm packages.

The final statement imports the CSS related to our <App /> component. Note that there is no variable name and no from directive. This is called a side-effect import — it doesn't import any value into the JavaScript file, but it tells Vite to add the referenced CSS file to the final code output, so that it can be used in the browser.
