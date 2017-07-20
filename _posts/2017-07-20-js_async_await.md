---
layout: post
title: js_async_await.md
author: antoine-wdg-rmz
tags: [javascript]
---

Using promises in javascript can be a little painful.
If you use a recent enough revision of js, you can handle this differently.
For example, this code:

```js
function do_stuff(url) {
  return new Promise((resolve) => {
     fetch(url).then(response => {
       response.json().then(data => {
         resolve(data);
       });
     });
  });
}
```

Can be rewritten like this using async/await:
```js
async function do_stuff(url) {
  const response = await fetch(url);
  const data = await response.json();
  return data;
}
```

Marking a function `async` makes it return a promise. 
Putting `await` before a promise waits for it to resolve and returns 
the argument that would have been passed to `resolve`.

**WARNING**: this feature is not included in ES6, but can be added with plugins 
and is part of ES7.
This is understood by [many browsers](http://kangax.github.io/compat-table/es2016plus/).
