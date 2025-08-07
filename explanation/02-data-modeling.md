---
title: "Explanation: Data Modeling"
description: "An in-depth explanation of the data modeling system in the Gemini FullStack ADK."
---

# Explanation: Data Modeling

In the Gemini FullStack Application Development Kit (ADK), data modeling is the foundation of your application's backend. A well-defined data model is crucial for building a robust and scalable application. This document explains the concepts behind the ADK's data modeling system and how to use it effectively.

## The `schema.json` File

The heart of the data modeling system is the `schema.json` file, located in the root of your project. This file is where you define all of your application's data models in a simple, declarative JSON format. The ADK uses this file as a single source of truth for your data layer.

A simple `schema.json` file might look like this:

```json
{
  "models": [
    {
      "name": "Todo",
      "fields": {
        "text": "string",
        "completed": "boolean",
        "createdAt": "datetime"
      }
    }
  ]
}
```

This schema defines a single model named `Todo` with three fields.

## Models

A **model** represents a type of object in your application. For example, in a to-do application, you would have a `Todo` model. In a blog application, you might have `Post` and `Comment` models. Each model corresponds to a table in your database.

When you define a model in your `schema.json`, the ADK will automatically:
*   Create a database table for that model.
*   Generate a REST API for creating, reading, updating, and deleting instances of that model.
*   Provide a high-level ORM for interacting with the model in your code.

## Fields

Each model has a set of **fields**, which represent the properties of the model. For each field, you must specify a `name` and a `type`.

The ADK supports a variety of field types:

| Type              | Description                                                                 |
| ----------------- | --------------------------------------------------------------------------- |
| `string`          | A sequence of characters.                                                   |
| `text`            | A long string, suitable for storing large blocks of text.                   |
| `integer`         | A whole number.                                                             |
| `float`           | A number with a decimal point.                                              |
| `boolean`         | A `true` or `false` value.                                                  |
| `datetime`        | A date and time value.                                                      |
| `hashed_password` | A special type for storing passwords securely.                              |
| `relation`        | A relationship to another model.                                            |

### Field Options

You can also specify options for each field to add constraints and validations. For example:

```json
"fields": {
  "email": {
    "type": "string",
    "required": true,
    "unique": true
  },
  "status": {
    "type": "string",
    "default": "draft"
  }
}
```

In this example:
*   The `email` field is required and must be unique across all users.
*   The `status` field has a default value of `"draft"`.

## Relationships

Your models can be related to each other. The ADK supports three types of relationships:

1.  **One-to-One**: A `User` has one `Profile`.
2.  **One-to-Many**: A `Post` has many `Comments`.
3.  **Many-to-Many**: A `Student` has many `Courses`, and a `Course` has many `Students`.

You define relationships using the `relation` field type. For example, to create a one-to-many relationship between a `Post` and a `Comment`:

```json
// In the Post model
"fields": {
  "comments": {
    "type": "relation",
    "model": "Comment",
    "relationType": "one-to-many"
  }
}
```

When you define a relationship, the ADK will automatically add the necessary foreign keys to your database tables and provide methods for querying the related models.

## The `generate` Command

After you have defined your data models in `schema.json`, you need to run the `gemini-adk generate api` command. This command does two things:

1.  **Generates the API**: It creates the REST API endpoints for your models.
2.  **Creates Migrations**: It generates database migration files that will update your database schema to match your models.

By using a declarative data modeling system, the Gemini FullStack ADK simplifies the process of building and evolving your application's data layer. It allows you to focus on defining your data, and the ADK takes care of the rest.
