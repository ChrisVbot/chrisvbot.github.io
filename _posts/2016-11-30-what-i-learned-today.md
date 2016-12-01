---
layout: single
author_profile: true
title: What I learned today
---

In an effort to constantly learn something new, I am going to regularly post what I'm learning about. So without further ado, here's some cool stuff I learned or read about today:

Some excerpts from an article by Heydon Pickering in Smashing Magazine:

- ["Some types of CSS properties are not inherited by default, and some elements do not inherit some properties."](https://www.smashingmagazine.com/2016/11/css-inheritance-cascade-global-scope-new-old-worst-best-friends/?utm_source=frontendfocus&utm_medium=email#the-inherit-keyword). 
- ["Each time you come to creating a new component, if it introduces new elements, style those new elements with element selectors."](https://www.smashingmagazine.com/2016/11/css-inheritance-cascade-global-scope-new-old-worst-best-friends/?utm_source=frontendfocus&utm_medium=email#element-styles) Doing so will allow consistent theming across the app, and eliminates the need to rewrite CSS under a different namespace. 
- ["[...]margin should not be considered a property of elements but a property of the context of elements. That is, they should only come into play where elements meet."](https://www.smashingmagazine.com/2016/11/css-inheritance-cascade-global-scope-new-old-worst-best-friends/?utm_source=frontendfocus&utm_medium=email#layout). Note to self: make more use of the ["lobotomized owl selector"](http://alistapart.com/article/axiomatic-css-and-lobotomized-owls).
- [CSS modules exist and are pretty neat.](https://css-tricks.com/css-modules-part-1-need/)

---

[BEM](http://getbem.com/introduction/) - Block, Element and Modifier. 

---

[An example of how a service worker is installed:](https://developers.google.com/web/fundamentals/getting-started/primers/service-workers?utm_source=frontendfocus&utm_medium=email) 

```javascript
var CACHE_NAME = 'my-site-cache-v1';
var urlsToCache = [
  '/',
  '/styles/main.css',
  '/script/main.js'
];

self.addEventListener('install', function(event) {
  // Perform install steps
  event.waitUntil(
    caches.open(CACHE_NAME)
      .then(function(cache) {
        console.log('Opened cache');
        return cache.addAll(urlsToCache);
      })
  );
});
```
After a service worker is installed and the user navigates to a different page or refreshes, the service worker will begin to receive `fetch` events, e.g.:

```javascript
self.addEventListener('fetch', function(event) {
  event.respondWith(
    caches.match(event.request)
      .then(function(response) {
        // Cache hit - return response
        if (response) {
          return response;
        }
        return fetch(event.request);
      }
    )
  );
});
```
I must admit I haven't really wrapped my head around Service Workers yet, but I can definitely see the potential. 

---

["CSS variables are now handled in every major browser except one"](http://thenewcode.com/1161/Using-CSS-Variables-in-Site-Development?utm_source=frontendfocus&utm_medium=email). It's currently not available in Microsoft Edge or IE. 
Variable definitions are preceded with two dashes, and can be anything that consists of a word without any spaces:

```css
body { 
  --alert: #cb333b;
}
```

Later:

```css
h3 { color: var(--alert); }
```
I love it! Also of note, CSS variables can be used within @media queries.

---

Cool idea: ["statically typed PostgreSQL queries with Typescript."](http://cs.mcgill.ca/~mxia3/2016/11/18/Statically-typed-PostgreSQL-queries-and-typescript-schemats/?utm_source=postgresweekly&utm_medium=email) I used Typescript when creating my Angular 2 contact list [app](https://github.com/ChrisVbot/ang2-contact-list) and really came to appreciate it. 

---

Eric Elliot [says](https://medium.com/javascript-scene/native-apps-are-doomed-ac397148a2c0#.woy9n3511) you may not need to build a native app! Progressive web apps can be installed on the user's home screen and can operate like a native app. Many in the comments disagree. Is this the way of the future? All I know is: maybe.  

---

["for..of is a method, introduced in ES2015, for iterating over "iterable collections."](https://bitsofco.de/for-in-vs-for-of/). e.g:

```javascript
const array = ['a','b','c', 'd'];  
const iterator = array[Symbol.iterator]();  
console.log( iterator.next().value )  
console.log( iterator.next().value )  
console.log( iterator.next().value )  
console.log( iterator.next().value )

// Result: a, b, c, d
```
We could say for example: 

```javascript
for (variable of iterable) {  
    // do stuff
}
```
This doesn't work for Objects because they aren't iterable and therefore don't have a [Symbol.iterator] property. It does work well with Arrays and Strings, however, and is a more reliable way of looping through an Array in sequence (which `for...in` does not):

```javascript
const array = ['a', 'b', 'c', 'd'];  
for (let item of array) {  
    console.log(item)
}
// Result: a, b, c, d

const string = 'Ire Aderinokun';  
for (let character of string) {  
    console.log(character)
}
// Result: I, r, e, , A, d, e, r, i, n, o, k, u, n
```

---

Lots of front end focus today, though as usual I still have tons of tabs open in my browser that I need to get to! 

P.S: Markdown is p. cool. 
