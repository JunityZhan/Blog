---
external: false
title: Route and rendering in Nextjs and Reactjs
description: Route and rendering in Nextjs and Reactjs
date: 2023-10-13
---

It's a beautiful world out there.

After setting up my blog, I've been hesitant to start writing because I've been lazy and swamped with other tasks. However, I believe it's essential to jot things down, especially when my knowledge seems overwhelming. I'm not the type to take traditional notes, so I decided to treat my blog as a notepad.

------

## Notes on **Next.js** and **React.js**:

I began learning about Next.js starting with routing. In the tutorial I followed, routing was based on the "page" method, which means every file within the `page` directory corresponds to a route. But the modern Next.js now uses the "app" routing. Here, every folder inside the `app` directory is treated as a route. Personally, I find "app" routing more logical, as it can encapsulate more files within. For beginners like me, this seems more intuitive.

Here are a few key points about Next.js routing:

1. **File-Based Routing**: The route depends on the file's location. For example, if there's a `page.tsx` inside the `app/posts` folder, the associated route would be `www.xxx.com/posts`. Here, "page" is a fixed name.
2. **Dynamic Routes**: Such routes can be created. For instance, if there's a folder named `[postsId]` inside the `posts` directory, you can access `www.xxx.com/posts/123`, where "123" becomes the `postsId`. Now, it will access the `page.tsx` inside the `[postsId]` folder. In `page.tsx`, by adding `{ params }: { params: { postId: string } }` to the exported function, you can access the parameter within the function, like using a template to access `{params.postId}`.
3. **Array Routes**: Dynamic routes can also be constructed using `[...posts]`. Assuming this folder is in `app/comments/`, you can pass multiple values to the route, e.g., accessing `www.xxx.com/comments/1/2/3` would be equivalent to passing `["1","2","3"]`. Values can be retrieved in a function using `{ params }: { params: {posts: any} }` and then accessed in a template as `{params.posts.join(' ')}`.

Additionally, there's a concept of fetching and rendering data during page load. Surprisingly, I found this to be straightforward compared to Vue, where routing and many other things had to be set up. Although many prefer Axios, I only needed one line:

```javascript
const res = await fetch('https://dummyjson.com/posts')
```

Another thing to note is the `useState` and `useEffect` hooks. However, I found the official examples unhelpful. It seems these are only necessary for dynamic updates. Also, they aren't recommended under server-side components (server-side rendering). This is because server-side rendered components generate an HTML sent to the client. But updates are still possible on the server-side with streaming and dynamic rendering, which I don't fully understand yet.

> **Update**: I've somewhat grasped the concept. There's a process called "Hydrating". Originally, server-rendered HTML was static. But with `useState`, updates can occur, and the front-end changes instead of remaining a static HTML page.

Let's dive into some notes on **asynchronous operations** and **promises**:

1. `await` can only be used inside an `async` function. Without `async`, there's no need for `await`, as every line would be equivalent to using `await`.
2. During an `async` operation, there might be instances where a function is called and execution moves to the next line before the function completes. In such cases, the function should return a promise. Once the promise is resolved, you can use `.then()` to execute subsequent code.

I haven't delved into making local requests yet, but once I do, I hope to write another blog post on it.
