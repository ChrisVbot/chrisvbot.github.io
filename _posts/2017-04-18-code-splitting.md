---
layout: single
author_profile: true
title: Code splitting and React
---

Today I watched a [really great talk](https://www.youtube.com/watch?v=bb6RCrDaxhw) by Neehar Venugopal about code splitting and it really clarified what exactly it is and how it benefits users. I've struggled with grasping the logic of code splitting in the past, even after doing a couple tutorials, but this video just makes it very clear to me. After all, it's a pretty simple concept: for any given change in your code, users should only need to download the updated files, instead of having to re-download a huge bundle file that contains the code for React, ReactDOM, React Router, etc. Then, the code that doesn't change can just be cached forever (if needed). Also, it makes a lot of sense the way he describes how, in a lot of cases, something like a user dashboard is always downloaded, even if we don't know if a particular user will ever see that dashboard. That adds a lot of extra work to something like a mobile phone for someone who may not even need that resource at all. I think Neehar sums it up best when he says, "send only the minimum amount of JavaScript required. [...] Whatever it takes to show the user what you want him to see on the current screen, just send that down the wire." 

The latter part of the above quote can be achieved with the use of dynamic imports, which loads modules asynchronously and which appears to currently be in stage 3 of the ECMAScript spec. It's also supported now in Webpack 2, which is pretty cool! [Here's](http://2ality.com/2017/01/import-operator.html) a nice blog post about it by Axel Rauschmayer. Here's one of the examples Neehar uses in his talk (which logs to console):

```javascript
import a from './a';
a(); // hello I'm a!

const bPromise = import('./b');
bPromise.then(b => (
    b.default() // hello I'm b!
  )
.catch(e => console.error(e));
```

As you can see, the async module returns a promise. When the promise resolves, we have access to the module. In the Webpack implementation, you just need to load your synchronous script and it polyfills the async script by adding an async script tag to the head. 

The talk then goes on to how to use this feature in React - as you can see there's a lot packed in to a 24-minute talk. [Check it out!](https://www.youtube.com/watch?v=bb6RCrDaxhw)






