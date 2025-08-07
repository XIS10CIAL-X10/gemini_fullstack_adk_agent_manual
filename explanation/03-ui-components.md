---
title: "Explanation: UI Components"
description: "An in-depth explanation of the UI component model in the Gemini FullStack ADK."
---

# Explanation: UI Components

The user interface (UI) of a Gemini FullStack ADK application is built using a component-based architecture. This approach allows you to create reusable, self-contained pieces of UI that can be composed together to build complex user interfaces. This document explains the concepts behind the ADK's UI component model.

## What is a Component?

A **component** is a reusable piece of your application's UI. It can be as small as a button or as large as an entire page. Each component is responsible for rendering a part of the UI and managing its own state.

For example, you might have components for:
*   A navigation bar
*   A user profile card
*   A data grid
*   A sign-up form

By breaking down your UI into components, you can make your code more modular, reusable, and easier to maintain.

## The Component-Based Philosophy

The Gemini FullStack ADK's UI philosophy is heavily influenced by modern JavaScript frameworks like React. The core ideas are:

*   **Declarative UI**: You describe what your UI should look like for a given state, and the framework takes care of updating the DOM efficiently.
*   **Component Composition**: You build complex UIs by combining smaller, simpler components.
*   **State Management**: Each component can have its own internal state, which makes it easier to reason about your application's logic.

## The `src` Directory

All of your frontend code, including your UI components, lives in the `src` directory. The ADK provides a standard structure for this directory:

*   `src/index.js`: The entry point of your application.
*   `src/App.js`: The root component of your application.
*   `src/components/`: A directory for your reusable UI components.
*   `src/styles/`: A directory for your global CSS files.

## Creating a Component

Creating a new component is as simple as creating a new JavaScript file in the `src/components` directory. Here's an example of a simple `Button` component:

```javascript
// src/components/Button.js
import React from 'react';
import './Button.css';

function Button({ children, onClick, type = 'button' }) {
  const className = `button button--${type}`;
  return (
    <button className={className} onClick={onClick}>
      {children}
    </button>
  );
}

export default Button;
```

This component can then be used anywhere in your application:

```javascript
import Button from './components/Button';

function MyPage() {
  return (
    <div>
      <h1>Welcome!</h1>
      <Button onClick={() => alert('Clicked!')}>Click Me</Button>
    </div>
  );
}
```

## State and Props

Components have two main ways of managing data: **props** and **state**.

*   **Props** (short for "properties") are used to pass data from a parent component to a child component. Props are read-only, meaning that a component should not modify its own props.
*   **State** is used for data that is internal to a component and changes over time. When a component's state changes, it will re-render to reflect the new state.

Here's an example of a component that uses both props and state:

```javascript
import React, { useState } from 'react';

function Counter({ initialCount = 0 }) {
  const [count, setCount] = useState(initialCount);

  return (
    <div>
      <p>Count: {count}</p>
      <button onClick={() => setCount(count + 1)}>Increment</button>
    </div>
  );
}
```

In this example:
*   `initialCount` is a prop that is passed down from a parent component.
*   `count` is a piece of state that is managed by the `Counter` component itself.

## Styling Components

There are several ways to style your components in a Gemini FullStack ADK application:

*   **Global CSS**: You can add global styles to the `src/styles/main.css` file. These styles will apply to your entire application.
*   **CSS Modules**: You can create a separate CSS file for each component (e.g., `Button.css`). When you import the CSS file into your component, the class names will be scoped locally to that component, which prevents style conflicts.
*   **CSS-in-JS**: You can use a CSS-in-JS library (like styled-components) to write your CSS directly in your JavaScript files. This approach is great for creating dynamic styles that change based on the component's state.

The component-based architecture of the Gemini FullStack ADK provides a powerful and flexible way to build modern user interfaces. By mastering these concepts, you can create beautiful, interactive, and maintainable applications.
