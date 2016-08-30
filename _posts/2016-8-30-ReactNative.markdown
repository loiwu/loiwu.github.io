---
layout: post
title:  "React Native"
date:   2016-8-30 8:06:00 +0800
published:  true
categories: bbkit
---


Logic will get you from A to B. Imagination will take you everywhere

---

# Understanding React Native Fundamentals

- The Virtual DOM

when you research how React works, you'll eventually encounter someone explaining it in the following manner:
UI = f(data)


- Components and JSX

we have come across this great framework for making fast differences between the Virtual DOM and its native components. How do we tell React Native what UI to represent or when to change it? A React Native component is a simple, reusable, function-like object that enables us to describe the native mobile components we want to render. They will always contain properties, state, and a render method.

JavaScript XML (JSX) is an XML-like extension to the ECMAScript speci cation. It combines the component logic (JavaScript) and markup (DOM or Native UI) into a single  le.

- Props and state of components

Props

How do the components in the same component hierarchy communicate with each other? Data is passed down through properties commonly known as props. Props are considered to be immutable by convention and should never be modi ed directly. To pass a prop into a component, just add a camel-cased attribute to the component.

state

So now we can pass in the data, but what if the data changes, then how can we display these changes to the user? Components can optionally contain state, a mutable and private set of data. State is a great way to keep track of user input, asynchronous requests, and events. 


# Summary

The Virtual DOM handles all of the DOM manipulations for us behind the scenes. At the same time, it uses effcient diffing algorithms to minimize the number of calls to the DOM. We have also seen how JSX allows us to express our components declaratively and combine our application logic into a single file. By using props and state, we can pass the data through components and update them dynamically.


#About this post

update on Aug 30, 2016.

