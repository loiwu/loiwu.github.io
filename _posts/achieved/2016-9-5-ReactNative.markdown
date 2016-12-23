---
layout: post
title:  "React Native"
date:   2016-9-5 8:06:00 +0800
published:  false
categories: bbkit
---


Logic will get you from A to B. Imagination will take you everywhere

---

# Setting up your development environment for the first React Native application

React Native is a collection of JavaScript and Objective-C code plus supporting tools that allow to create, run, and debug native iOS applications.
In order to reach the point where we can actually start working on our first React Native application, some preparation is necessary.
On your development machine, the following components need to be made available:
• Homebrew
• io.js
• Watchman
• Google Chrome • React Native CLI

## Installing Homebrew

Homebrew is a package manager for Mac OS X. We will use it to subsequently install most of the software tools we need.
In order to install and set up Homebrew, open a Terminal shell window and run the following command:
ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
For further information, visit the Homebrew homepage at http://brew.sh/.

## Installing io.js

io.js is a modern fork of Node.js, the popular server-side JavaScript runtime environment. React Native ships with some helper tools that are written for io.js. Also, we will regularly use the Node.js/io.js package manager, NPM, to install the React Native command line tool and other dependencies.
We are not going to install io.js directly. Instead, we will use Homebrew to install nvm, the Node Version Manager.

nvm is a nifty little tool that takes the hassle out of managing parallel installs of different versions of Node.js and/or io.js. With it, you can install as many versions of Node.js and io.js as you wish, and quickly switch to the version you want to actually use for a given project.
In order to install and set up nvm, open a Terminal window and run the following command:
brew install nvm
Afterwards, create or open file $HOME/.bashrc, and add the following lines at the beginning: export NVM_DIR=~/.nvm
source $(brew --prefix nvm)/nvm.sh
Close the Terminal session, and start Terminal anew - you now have nvm enabled in your Terminal session.
Using nvm, we can now install io.js, like this:
nvm install iojs
nvm alias default iojs
This will install and setup the most recent stable version of io.js, plus the matching version of NPM, the Node Package Manager, and make this setup the default.

## Installing Watchman

React Native uses Watchman to monitor and react to changes in source code files. This is explained in more detail in a later chapter.
In order to install and set up Watchman, open a Terminal window and run the following command:
brew install --HEAD watchman
The --HEAD parameter ensures that the most recent version of Watchman is installed.

## Installing Google Chrome

Google Chrome isn’t strictly necessary to create applications with React Native, but it allows to debug them during development. The details are explained in a later chapter.
Head over to https://www.google.com/chrome/browser/desktop/index.html to download the latest version.

## Installing the React Native CLI

The React Native Command Line Interface is a small io.js helper script that allows to set up new React Native projects.
In order to install and set up React Native CLI, open a Terminal window and run the following command:
npm install -g react-native-cli

With this, we are good to go to create our first application.

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

---

#About this post

update on Sep 5, 2016.

