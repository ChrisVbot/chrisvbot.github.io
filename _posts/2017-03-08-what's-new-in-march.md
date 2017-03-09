---
layout: single
author_profile: true
title: What's new in March
---

Haven't updated in a while, but I'm back with another update! 

My most recent project at work is nearing completion. It's a fairly simple React single page app that I put together to learn and teach React, Webpack(1 and 2), ES6, and Redux. I've learned a lot while working on this project, especially in terms of how React works and how it can be used in conjunction with Redux to manage state. 

At first glance, learning React was pretty intimidating. I remember trying to learn it for my final project at Lighthouse Labs and just not getting it at all, no matter how many tutorials I read or watched. Of course, the best way to learn is to just jump right in, and soon enough I was able to wrap my head around it and realized that React is a relatively simple view library at its core. That said, I'm grateful that I previously learned how Angular 2 works in terms of splitting an app into components. While Angular 2 is a pretty different beast than React, working with it gave me a pretty solid foundation in component-style thinking. 

React is pretty neat. I like the concept of passing data via props and how changes to the state are detected via the shadow DOM. JSX is very straightforward to work with, and makes logical sense to me. The ability to do inline styling is also pretty great, but I also really enjoy creating localized, modular CSS files for each component and generating unique class names for them. 

Moving on to Redux, it took me a little while to grasp the concepts. Looking at example code on Github would often leave me scratching my head trying to piece together all the pieces of the puzzle that go into action creators, reducers, dispatches, etc. I watched numerous tutorials and was still not quite getting it, but as usual, the best way to learn is just by doing. Once I wrote some simple Redux code, it eventually just clicked and made sense to me. I still think it would be pretty challenging to take a look at a completed, complex app and piece together the Redux parts, but given some time with the app, I think it would eventually become clear. Redux, like React, is pretty simple at its core, but that of course doesn't always translate to being easy to learn! I definitely appreciate the ability to manage the state in a single state tree, and I gained a better understanding of functional programming as well. The ability to use middleware is very cool as well, and I really liked using logger and thunk. 

As for ES6, I like it quite a bit. It seems one of my next projects at work will be to create a course on ES6 and I'm looking forward to it. While I used ES6 in my previous Angular 2 app, I am starting to feel more comfortable using it. Arrow functions are super cool, as are classes, let + const, and destructuring. Love destructuring! There's a lot more to ES6 that I'm eager to dig into as well (especially looking to work more with promises). I'd also like to give a big shout out to [Babel](https://babeljs.io/) which I think is just amazing. 

Webpack 2 was officially released shortly after I started recording my course which was a bit unfortunate in terms of timing. This actually turned out pretty well, since I was able to demo (and learn!) using both Webpack 1 and 2. I created most of my app using Webpack 1 while incrementally building the Webpack config file out (e.g. adding CSS loaders when appropriate, adding hot module reloading, updating Babel config to use rest-spread operator, etc). Later, when the project was almost completed, I was able to demonstrate the procedure of updating to Webpack 2 which of course required me to update my config file and implement React Hot Loader 3 which is still in beta. That meant also updating to Webpack-dev-server @beta version as recommended by the [Webpack 2 docs](https://webpack.js.org/guides/hmr-react/). Overall, I'd say I have a solid grasp of Webpack but am looking forward to spending a lot more time with it - next I'd like to incorporate SASS usage, code splitting, and minification.

Definitely excited to work more with React, Redux, and Webpack going forward!

