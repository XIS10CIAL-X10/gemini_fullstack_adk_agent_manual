---
title: "End-to-End: Building a To-Do Application"
description: "A 15-minute tutorial on building a complete To-Do application with a frontend and backend using the Gemini FullStack ADK."
---

# End-to-End: Building a To-Do Application

In this tutorial, you will build a complete "To-Do" application from scratch using the Gemini FullStack ADK. You'll create a frontend to manage your to-do items and a backend to store them.

**Time to complete:** 15 minutes

## What you'll build

You'll build a simple web application that allows you to:
*   View a list of to-do items.
*   Add new to-do items to the list.
*   Mark to-do items as complete.

## Before you begin

Make sure you have completed the **[Hello, World!](./01-hello-world.md)** tutorial. You should have a basic understanding of how to create and run a Gemini FullStack ADK project.

## 1. Create a new project

Start by creating a new project for your to-do application.

```bash
gemini-adk new todo-app
cd todo-app
```

## 2. Define the data model

First, you need to define the data model for your to-do items. In the Gemini FullStack ADK, you can define your data models in a schema file.

Open the `schema.json` file in your project's root directory and replace its content with the following:

```json
{
  "models": [
    {
      "name": "Todo",
      "fields": {
        "text": "string",
        "completed": "boolean"
      }
    }
  ]
}
```

<details>
<summary>What does this schema do?</summary>

This schema defines a `Todo` model with two fields: `text` (a string) and `completed` (a boolean). The ADK will use this schema to automatically generate a REST API for your data model and set up a database for you.
</details>

## 3. Generate the API

After defining your data model, you can use the ADK to generate the backend API.

Run the following command:

```bash
gemini-adk generate api
```

This command inspects your `schema.json` file and creates API endpoints for creating, reading, updating, and deleting to-do items.

## 4. Create the frontend

Now let's build the user interface for your application. The ADK uses a component-based approach for building frontends.

Replace the content of `src/App.js` with the following code:

```javascript
import React, { useState, useEffect } from 'react';

function App() {
  const [todos, setTodos] = useState([]);
  const [text, setText] = useState('');

  useEffect(() => {
    fetch('/api/todos')
      .then(response => response.json())
      .then(data => setTodos(data));
  }, []);

  const addTodo = (e) => {
    e.preventDefault();
    fetch('/api/todos', {
      method: 'POST',
      headers: { 'Content-Type': 'application/json' },
      body: JSON.stringify({ text, completed: false }),
    })
      .then(response => response.json())
      .then(newTodo => {
        setTodos([...todos, newTodo]);
        setText('');
      });
  };

  const toggleTodo = (id, completed) => {
    fetch(`/api/todos/${id}`, {
      method: 'PUT',
      headers: { 'Content-Type': 'application/json' },
      body: JSON.stringify({ completed: !completed }),
    })
      .then(() => {
        setTodos(todos.map(todo =>
          todo.id === id ? { ...todo, completed: !completed } : todo
        ));
      });
  };

  return (
    <div>
      <h1>To-Do List</h1>
      <form onSubmit={addTodo}>
        <input
          type="text"
          value={text}
          onChange={(e) => setText(e.target.value)}
          placeholder="Add a new to-do"
        />
        <button type="submit">Add</button>
      </form>
      <ul>
        {todos.map(todo => (
          <li
            key={todo.id}
            onClick={() => toggleTodo(todo.id, todo.completed)}
            style={{ textDecoration: todo.completed ? 'line-through' : 'none' }}
          >
            {todo.text}
          </li>
        ))}
      </ul>
    </div>
  );
}

export default App;
```

## 5. Test your application

The Gemini FullStack ADK encourages testing from the start. A sample test file is created for you at `src/App.test.js`. Replace its content with this test for your to-do list:

```javascript
import React from 'react';
import { render, screen, fireEvent } from '@testing-library/react';
import App from './App';

test('renders to-do list and adds a new item', () => {
  render(<App />);

  // Check for the heading
  expect(screen.getByText('To-Do List')).toBeInTheDocument();

  // Add a new to-do
  const input = screen.getByPlaceholderText('Add a new to-do');
  fireEvent.change(input, { target: { value: 'Test the app' } });
  fireEvent.click(screen.getByText('Add'));

  // This is a simplified test. In a real app, you would mock the fetch calls.
  // For now, we'll just check if the input is cleared.
  expect(input.value).toBe('');
});
```

To run the tests, use the following command:

```bash
gemini-adk test
```

All tests should pass.

## 6. Run your application

Now, let's see your application in action.

```bash
gemini-adk run
```

Open your browser and go to `http://localhost:8080`. You should see your to-do application. Try adding a new item and marking it as complete.

🎉 **Well done!** You have successfully built a full-stack application with the Gemini FullStack ADK.

## Common Pitfalls & FAQs

*   **API errors**: If you see errors related to the API, make sure you have run `gemini-adk generate api` after modifying your `schema.json`.
*   **CORS issues**: The built-in development server is configured to avoid Cross-Origin Resource Sharing (CORS) issues. If you deploy your application, you may need to configure CORS on your server.

## Further Reading

*   **[How-to: Deploy Your Application](../how-tos/01-deployment.md)**: Learn how to deploy your application to a production environment.
*   **[Data Modeling (explanation)](../explanation/02-data-modeling.md)**: An in-depth guide to defining data models in the Gemini FullStack ADK.
