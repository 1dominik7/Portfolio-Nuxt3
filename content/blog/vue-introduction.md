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

# Introduction to Vue 3

![Vue 3 Introduction](/images/vue-logo.png)

## What is Vue 3?

Vue.js 3 is a progressive JavaScript framework for building user interfaces on the web. It's designed to be incrementally adoptable and can easily scale between a library and a full-featured framework.

---

## Why Choose Vue 3?

Vue 3 comes with several exciting features that make it an excellent choice for developers:

- **Composition API:** This new API provides a set of additive, function-based APIs that allow flexible composition of component logic.

- **Faster rendering:** Vue 3 features a faster virtual DOM and improved runtime performance.

- **Improved TypeScript support:** Vue 3's codebase is written in TypeScript, allowing for better TypeScript integration.

- **Smaller Bundle Size:** Another significant improvement in Vue.js 3 is the smaller bundle size. The new version of Vue.js has been optimized for a smaller bundle size, which means it takes up less space in your application. This can help to reduce the loading time of your application, making it more responsive and efficient.

- **Better Reactivity System:** Vue.js 3 also comes with a new reactivity system that is designed to make it easier to manage the state of your application. With this new reactivity system, Vue.js 3 provides better support for reactive programming and makes it easier to create reactive components. This can help to simplify your code and make it more efficient, reducing the amount of work needed to create reactive components.

---

## Getting Started with Vue 3

Here's a basic Vue 3 application setup:

```javascript
const { createApp } = Vue;
const app = createApp({
  data() {
    return {
      message: "Hello Vue 3!",
    };
  },
});
app.mount("#app");
```

Using the ES Module Build
​
Throughout the rest of the documentation, we will be primarily using ES modules syntax. Most modern browsers now support ES modules natively, so we can use Vue from a CDN via native ES modules like this:

```javascript
<div id="app">{{ message }}</div>

<script type="module">
  import { createApp, ref } from 'https://unpkg.com/vue@3/dist/vue.esm-browser.js'

  createApp({
    setup() {
      const message = ref('Hello Vue!')
      return {
        message
      }
    }
  }).mount('#app')
</script>
```