---
title: "How to Customize the User Interface"
description: "A guide on customizing the user interface of your Gemini FullStack ADK application."
---

# How to Customize the User Interface

The Gemini FullStack ADK provides a default user interface (UI) to help you get started quickly. However, you'll likely want to customize the UI to match your brand and create a unique user experience. This guide will show you how.

## Quick Start

Here are the main ways to customize the UI:

1.  **Modify the CSS**: Edit the global CSS file at `src/styles/main.css`.
2.  **Change the Layout**: Modify the main layout component at `src/components/Layout.js`.
3.  **Create New Components**: Build your own reusable UI components.

## Modifying the CSS

The simplest way to change the look and feel of your application is to modify the global CSS file at `src/styles/main.css`. You can add your own CSS rules here to override the default styles.

For example, to change the primary color of your application, you could add the following CSS:

```css
:root {
  --primary-color: #007bff; /* A nice blue */
}

body {
  font-family: 'Roboto', sans-serif;
}
```

<details>
<summary>Where do the default styles come from?</summary>

The Gemini FullStack ADK uses a lightweight, modern CSS framework to provide sensible defaults for your application's UI. This framework is designed to be easily customizable and extendable.
</details>

## Changing the Layout

The main layout of your application is defined in the `src/components/Layout.js` component. This component is responsible for the overall structure of your pages, such as the header, footer, and navigation.

You can edit this file to change the layout. For example, you could add a sidebar to your application:

```javascript
import React from 'react';
import Header from './Header';
import Footer from './Footer';
import Sidebar from './Sidebar';

function Layout({ children }) {
  return (
    <div className="layout">
      <Header />
      <div className="main-content">
        <Sidebar />
        <main>{children}</main>
      </div>
      <Footer />
    </div>
  );
}

export default Layout;
```

## Creating New Components

For more complex UI changes, you'll want to create your own reusable components. The ADK is designed to work seamlessly with popular frontend libraries like React.

You can create a new component by adding a new file to the `src/components` directory. For example, you could create a `Button.js` component with your own custom styling:

```javascript
import React from 'react';
import './Button.css';

function Button({ children, onClick }) {
  return (
    <button className="custom-button" onClick={onClick}>
      {children}
    </button>
  );
}

export default Button;
```

You can then use this component throughout your application.

## Common Pitfalls & FAQs

*   **CSS Specificity**: If your CSS rules are not being applied, it might be due to CSS specificity. You may need to use more specific selectors to override the default styles.
*   **Component Libraries**: The ADK is compatible with popular component libraries like Material-UI and Bootstrap. You can install them via npm and import them into your project.

## Further Reading

*   **[State Management (how-to)](./06-state-management.md)**: Learn how to manage the state of your application's UI.
*   **[UI Components (explanation)](../explanation/05-ui-components.md)**: A deeper dive into the component-based UI system of the Gemini FullStack ADK.
