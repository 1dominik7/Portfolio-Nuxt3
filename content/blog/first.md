---
description: "meta description of the page"
head:
  meta:
    - name: "keywords"
      content: "nuxt, vue, content"
    - name: "robots"
      content: "index, follow"
    - name: "author"
      content: "NuxtLabs"
    - name: "copyright"
      content: "© 2022 NuxtLabs"
    - name: "og:title"
      content: "This is an OpenGraph title"
publishedAt: 2023-04-12 15:20:00
toc: true
---

# React 19 RC

## React 19 RC is now available on npm!

In our React 19 RC Upgrade Guide, we shared step-by-step instructions for upgrading your app to React 19. In this post, we’ll give an overview of the new features in React 19, and how you can adopt them.

• What’s new in React 19\
• Improvements in React 19\
• How to upgrade

## What’s new in React 19

**Actions**

A common use case in React apps is to perform a data mutation and then update state in response. For example, when a user submits a form to change their name, you will make an API request, and then handle the response. In the past, you would need to handle pending states, errors, optimistic updates, and sequential requests manually.

For example, you could handle the pending and error state in useState:

```javascript
// Before Actions
function UpdateName({}) {
  const [name, setName] = useState("");
  const [error, setError] = useState(null);
  const [isPending, setIsPending] = useState(false);

  const handleSubmit = async () => {
    setIsPending(true);
    const error = await updateName(name);
    setIsPending(false);
    if (error) {
      setError(error);
      return;
    }
    redirect("/path");
  };

  return (
    <div>
      <input value={name} onChange={(event) => setName(event.target.value)} />
      <button onClick={handleSubmit} disabled={isPending}>
        Update
      </button>
      {error && <p>{error}</p>}
    </div>
  );
}
```

In React 19, we’re adding support for using async functions in transitions to handle pending states, errors, forms, and optimistic updates automatically.

For example, you can use useTransition to handle the pending state for you:

```javascript
// Using pending state from Actions
function UpdateName({}) {
  const [name, setName] = useState("");
  const [error, setError] = useState(null);
  const [isPending, startTransition] = useTransition();

  const handleSubmit = () => {
    startTransition(async () => {
      const error = await updateName(name);
      if (error) {
        setError(error);
        return;
      } 
      redirect("/path");
    })
  };

  return (
    <div>
      <input value={name} onChange={(event) => setName(event.target.value)} />
      <button onClick={handleSubmit} disabled={isPending}>
        Update
      </button>
      {error && <p>{error}</p>}
    </div>
  );
}
```

The async transition will immediately set the isPending state to true, make the async request(s), and switch isPending to false after any transitions. This allows you to keep the current UI responsive and interactive while the data is changing.

Building on top of Actions, React 19 introduces useOptimistic to manage optimistic updates, and a new hook React.useActionState to handle common cases for Actions. In react-dom we’re adding <form> Actions to manage forms automatically and useFormStatus to support the common cases for Actions in forms.

In React 19, the above example can be simplified to:
```javascript
// Using <form> Actions and useActionState
function ChangeName({ name, setName }) {
  const [error, submitAction, isPending] = useActionState(
    async (previousState, formData) => {
      const error = await updateName(formData.get("name"));
      if (error) {
        return error;
      }
      redirect("/path");
      return null;
    },
    null,
  );

  return (
    <form action={submitAction}>
      <input type="text" name="name" />
      <button type="submit" disabled={isPending}>Update</button>
      {error && <p>{error}</p>}
    </form>
  );
}
```
In the next section, we’ll break down each of the new Action features in React 19.

**New hook: useActionState**

To make the common cases easier for Actions, we’ve added a new hook called useActionState:

```javascript
const [error, submitAction, isPending] = useActionState(
  async (previousState, newName) => {
    const error = await updateName(newName);
    if (error) {
      // You can return any result of the action.
      // Here, we return only the error.
      return error;
    }

    // handle success
    return null;
  },
  null,
);
```

useActionState accepts a function (the “Action”), and returns a wrapped Action to call. This works because Actions compose. When the wrapped Action is called, useActionState will return the last result of the Action as data, and the pending state of the Action as pending 
**and many more, check [all changes](https://react.dev/blog/2024/04/25/react-19).**
