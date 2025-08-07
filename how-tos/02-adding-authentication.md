---
title: "How to Add User Authentication"
description: "A guide on adding user authentication to your Gemini FullStack ADK application."
---

# How to Add User Authentication

This guide explains how to add user authentication to your application. The Gemini FullStack ADK provides a built-in authentication module that makes it easy to secure your app and manage users.

## Quick Start

Adding authentication is as simple as running a single command:

```bash
gemini-adk add auth
```

This command will:
*   Add a `User` model to your `schema.json`.
*   Generate API endpoints for user registration, login, and logout.
*   Create frontend components for sign-up and sign-in forms.

## The `User` Model

The `gemini-adk add auth` command adds a `User` model to your `schema.json` file. It looks like this:

```json
{
  "name": "User",
  "fields": {
    "email": "string",
    "password": "hashed_password"
  }
}
```

The `hashed_password` field type is a special type provided by the ADK that automatically handles password hashing and verification.

<details>
<summary>Why is password hashing important?</summary>

Password hashing is a critical security measure. It converts a user's password into a fixed-length string of characters, which is then stored in the database. This means that even if your database is compromised, the attacker will not be able to see the users' actual passwords.
</details>

## Frontend Components

After running the command, you'll find new frontend components in your `src/components/auth` directory. You can use these components to create sign-up and sign-in pages in your application.

Here's an example of how you might use the `LoginForm` component in your `App.js`:

```javascript
import React from 'react';
import LoginForm from './components/auth/LoginForm';

function App() {
  return (
    <div>
      <h1>Welcome to My App</h1>
      <LoginForm />
    </div>
  );
}

export default App;
```

## Securing API Endpoints

To secure an API endpoint, you can add an `auth: true` property to its definition in your `routes.json` file.

```json
{
  "routes": [
    {
      "path": "/api/protected-data",
      "handler": "getProtectedData",
      "auth": true
    }
  ]
}
```

When `auth` is set to `true`, the ADK will ensure that only authenticated users can access that endpoint.

## Common Pitfalls & FAQs

*   **Customizing Forms**: The default authentication forms are basic. You can customize them by editing the files in `src/components/auth`.
*   **Social Logins**: The built-in authentication module supports social logins (e.g., Google, GitHub). You can configure them in the `config.json` file.

## Further Reading

*   **[User Profiles (how-to)](./05-user-profiles.md)**: Learn how to extend the `User` model to include user profile information.
*   **[Authentication (explanation)](../explanation/04-authentication.md)**: A more detailed explanation of the authentication system in the Gemini FullStack ADK.
