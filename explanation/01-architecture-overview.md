---
title: "Architecture Overview"
description: "An explanation of the core architecture of the Gemini FullStack ADK."
---

# Architecture Overview

The Gemini FullStack Application Development Kit (ADK) is designed with a modern, modular architecture that promotes a clean separation of concerns and a streamlined development workflow. This document provides a high-level overview of the key components of a Gemini FullStack ADK application and how they interact with each other.

## Core Philosophy

Our architectural philosophy is guided by three main principles:

1.  **Convention over Configuration**: The ADK provides sensible defaults and a clear project structure, allowing you to focus on writing your application's logic instead of getting bogged down in configuration.
2.  **Separation of Concerns**: We enforce a strong separation between the frontend, backend, and data layers of your application. This makes your codebase easier to understand, maintain, and scale.
3.  **Developer Experience**: We believe that a great developer experience leads to great applications. The ADK is designed to be intuitive, with a powerful CLI and a fast development server that supports hot-reloading.

## The Three Layers

A typical Gemini FullStack ADK application is composed of three distinct layers: the **Frontend Layer**, the **Backend Layer**, and the **Data Layer**.

![Three-layer architecture diagram](https://via.placeholder.com/800x300.png?text=Frontend+<->+Backend+<->+Data)
*(A diagram showing the three layers of the architecture: Frontend, Backend, and Data, with arrows indicating communication between them.)*

### 1. Frontend Layer

The frontend layer is what your users interact with. It's responsible for rendering the user interface and handling user input.

*   **Technology**: The ADK uses a modern, component-based JavaScript framework (like React) for building user interfaces.
*   **Structure**: Frontend code is located in the `src` directory. You'll find your main application component at `src/App.js` and reusable UI components in `src/components`.
*   **Communication**: The frontend communicates with the backend layer via a REST API. It sends HTTP requests to the backend to fetch and manipulate data.

### 2. Backend Layer

The backend layer is the engine of your application. It's responsible for handling business logic, processing data, and responding to requests from the frontend.

*   **Technology**: The backend is built on a high-performance, compiled language that ensures your application is fast and scalable.
*   **Structure**: Backend code is typically defined through high-level configuration files, such as `routes.json` for defining API routes and `schema.json` for data modeling. The ADK uses these files to generate the actual backend code.
*   **API**: The backend exposes a REST API that the frontend consumes. The ADK can automatically generate this API based on your data models, saving you significant development time.

### 3. Data Layer

The data layer is responsible for persisting and retrieving your application's data.

*   **Technology**: The ADK uses a relational database (like PostgreSQL) to store your data. It provides an Object-Relational Mapping (ORM) layer that allows you to interact with the database using simple, high-level code.
*   **Data Modeling**: You define your data models in the `schema.json` file. The ADK uses this schema to create and manage your database tables.
*   **Migrations**: The ADK automatically handles database migrations. When you change your data models, the ADK will generate and apply the necessary database schema changes.

## The Development Workflow

The Gemini FullStack ADK is designed to make the development workflow as smooth as possible. Here's a typical workflow:

1.  **Model your data**: Define your data models in `schema.json`.
2.  **Generate your API**: Use `gemini-adk generate api` to create your backend API.
3.  **Build your UI**: Create your frontend components in the `src` directory.
4.  **Run and test**: Use `gemini-adk run` to start the development server and `gemini-adk test` to run your tests.
5.  **Deploy**: When you're ready, use `gemini-adk deploy` to deploy your application to the cloud.

This architecture provides a solid foundation for building robust, scalable, and maintainable full-stack applications. By understanding these core concepts, you'll be well-equipped to get the most out of the Gemini FullStack ADK.
