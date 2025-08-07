---
title: "How to Deploy Your Application"
description: "A guide on deploying your Gemini FullStack ADK application to the cloud."
---

# How to Deploy Your Application

This guide will show you how to deploy your Gemini FullStack ADK application to a production environment. We'll use the fictional "Gemini Cloud" for this example, but the principles can be applied to other cloud providers as well.

## Quick Start

Deploying your application is a straightforward process with the Gemini FullStack ADK. Here are the steps:

1.  **Log in to Gemini Cloud**:
    ```bash
    gemini-adk login
    ```
2.  **Build your application for production**:
    ```bash
    gemini-adk build --production
    ```
3.  **Deploy the application**:
    ```bash
    gemini-adk deploy
    ```

That's it! Your application is now live.

## Building for Production

The `gemini-adk build --production` command creates an optimized build of your application. It performs several tasks to get your app ready for deployment:

*   **Frontend**: Minifies your JavaScript and CSS, and optimizes images.
*   **Backend**: Compiles your server-side code into a highly efficient binary.
*   **Database**: Prepares database migration scripts.

<details>
<summary>Why is a production build important?</summary>

A production build is optimized for performance and security. It removes debugging information, reduces file sizes, and applies other optimizations to ensure your application runs smoothly and efficiently for your users.
</details>

## The Deployment Process

When you run `gemini-adk deploy`, the ADK handles all the complexities of deployment for you:

1.  **Provisioning Resources**: It provisions the necessary cloud resources, such as a server, a database, and a load balancer.
2.  **Uploading Files**: The optimized build files are uploaded to the server.
3.  **Running Migrations**: The database migration scripts are executed to set up the database schema.
4.  **Starting the Application**: The application server is started.
5.  **Configuring DNS**: The DNS records are updated to point to your new application.

## Common Pitfalls & FAQs

*   **Authentication Failed**: If you get an authentication error, make sure you have logged in with `gemini-adk login` and that your credentials are correct.
*   **Deployment Failed**: If the deployment fails, check the logs for more information. You can view the deployment logs with the following command:
    ```bash
    gemini-adk logs --deployment
    ```

## Further Reading

*   **[Custom Domains (how-to)](./04-custom-domains.md)**: Learn how to configure a custom domain for your deployed application.
*   **[CI/CD Integration (explanation)](../explanation/03-ci-cd.md)**: An in-depth look at integrating the Gemini FullStack ADK with your continuous integration and deployment pipeline.
