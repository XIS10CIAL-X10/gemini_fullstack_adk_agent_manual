---
title: "Hello, World!: Your First Gemini FullStack App"
description: "A 5-minute tutorial on creating and running a 'Hello, World!' application using the Gemini FullStack ADK."
---

# Hello, World!: Your First Gemini FullStack App

Welcome to the Gemini FullStack ADK! This tutorial will guide you through creating and running a simple "Hello, World!" application. It's a great way to get a feel for how the ADK works.

**Time to complete:** 5 minutes

## Before you begin

Make sure you have the Gemini FullStack ADK installed on your system. If you haven't installed it yet, please refer to the installation guide (link to be added).

## 1. Create a new project

First, you'll create a new project. The ADK provides a command to generate a new project with a basic structure.

Open your terminal and run the following command:

```bash
gemini-adk new hello-world
```

This command creates a new directory named `hello-world` with all the necessary files to get you started.

<details>
<summary>What does this command do?</summary>

The `gemini-adk new` command scaffolds a new project for you. It creates a directory with a default project structure, including configuration files and a sample application. This saves you from having to set up everything manually.
</details>

## 2. Navigate to the project directory

Next, move into the newly created project directory:

```bash
cd hello-world
```

All subsequent commands should be run from within this directory.

## 3. Run the application

Now you're ready to run your "Hello, World!" application. The ADK comes with a built-in development server that makes it easy to run your app locally.

Start the development server with this command:

```bash
gemini-adk run
```

You should see output in your terminal indicating that the server is running.

## 4. View your application

Open your web browser and navigate to `http://localhost:8080`. You should see a page with the message "Hello, World!".

🎉 **Congratulations!** You've just created and run your first Gemini FullStack application.

## Common Pitfalls & FAQs

*   **Port already in use**: If you get an error that port 8080 is already in use, you can specify a different port using the `--port` flag:
    ```bash
    gemini-adk run --port 8081
    ```
*   **Command not found**: If your terminal can't find the `gemini-adk` command, make sure you have installed the ADK correctly and that it's in your system's PATH.

## Further Reading

*   **[End-to-End Application](./02-end-to-end-app.md)**: Ready for a more in-depth tutorial? Build a complete application.
*   **[Project Structure (explanation)](../explanation/01-project-structure.md)**: Learn more about the files and directories in a Gemini FullStack ADK project.
