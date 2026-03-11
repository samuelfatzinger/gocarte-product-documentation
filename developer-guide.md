# GoCarte Developer Guide

## Overview

The GoCarte API allows developers to integrate project and task management functionality into external applications. Using the API, developers can create projects, generate tasks, and update project progress from other systems.

This guide demonstrates a typical integration workflow. The example scenario shows how an external application might create a project, add tasks, and update task progress using the GoCarte API.

For detailed endpoint specifications, parameters, and response formats, refer to the **GoCarte API Reference**.

---

# Common Integration Use Cases

Developers often use the GoCarte API to connect GoCarte with other tools or internal systems. These integrations automate routine project management tasks or synchronize project and task information across platforms.

Common examples include the following.

## Automated Task Creation

External systems can automatically create tasks in GoCarte when specific events occur.

For example, a customer support platform may create a GoCarte task when a bug report or service ticket is submitted.

## Workflow Automation

Teams sometimes use the API to automate project setup. When a new initiative begins, such as a marketing campaign or product release, an integration can create a GoCarte project and generate a standard set of tasks for the team.

Tasks can also be duplicated across projects. For example, a routine automation check for daily sales numbers could be defined as a task and reused across multiple projects.

## Integration with Development Pipelines

Development teams may connect GoCarte with version control or deployment systems. For instance, a continuous integration pipeline might update task status in GoCarte when a build completes or a feature is deployed.

## Reporting and Internal Dashboards

Organizations sometimes use the GoCarte API to retrieve project data for internal reporting systems. This allows them to track project progress, task completion, and team activity without working directly inside the GoCarte interface.

---

# Prerequisites

Before integrating with the GoCarte API, ensure that the following requirements are met.

- A valid GoCarte account  
- An API key generated through GoCarte developer settings  
- Familiarity with REST APIs and HTTP requests  
- A tool capable of sending HTTP requests, such as Postman, curl, or a programming language HTTP client  

---

# Typical Integration Workflow

Many integrations follow a similar sequence of steps:

1. Authenticate with the GoCarte API  
2. Retrieve existing projects in a Workroom  
3. Create a project if one does not already exist  
4. Create tasks associated with that project  
5. Update task progress as work is completed  

The sections below demonstrate this workflow.

---

# Step 1: Authenticate with the API

All API requests require authentication using an API key.

Include the API key in the **Authorization header** of every request.

Example:

```
Authorization: Bearer YOUR_API_KEY
```

Requests without a valid API key return a **401 Unauthorized** response.

Applications typically store API keys securely and attach them automatically to each request.

---

# Step 2: Retrieve Existing Projects

Integrations often begin by retrieving the list of existing projects within a Workroom. This allows the application to determine whether a project already exists before creating a new one.

Example request:

```
GET https://api.gocarte.com/v1/projects
```

Example response:

```json
{
  "projects": [
    {
      "id": "prj_1042",
      "name": "Website Redesign",
      "status": "active"
    }
  ]
}
```

This request returns a list of projects associated with the authenticated Workroom.

Applications can use this information to display project data or determine whether a new project should be created.

---

# Step 3: Create a Project

If an appropriate project does not already exist, the integration can create one.

Example request:

```
POST https://api.gocarte.com/v1/projects
```

Example request body:

```json
{
  "name": "Product Launch",
  "description": "Planning tasks for upcoming release"
}
```

Successful requests return a **201 Created** response.

Applications often use this endpoint to automatically generate projects when new initiatives or workflows begin.

---

# Step 4: Create Tasks

After creating a project, tasks can be generated programmatically.

Example request:

```
POST https://api.gocarte.com/v1/tasks
```

Example request body:

```json
{
  "project_id": "prj_1042",
  "title": "Design landing page",
  "assigned_to": "user_301",
  "due_date": "2025-05-15"
}
```

Successful requests return a **201 Created** response.

Integrations often use this endpoint to create tasks automatically from external systems such as ticketing platforms or content management systems.

---

# Step 5: Update Task Progress

External systems can update task progress by modifying the task status.

Example request:

```
PATCH https://api.gocarte.com/v1/tasks/{task_id}
```

Example request body:

```json
{
  "status": "In Progress"
}
```

Successful requests return a **200 OK** response.

Updating task status allows external systems to synchronize work progress with GoCarte dashboards.

---

# Integration Best Practices

When building integrations with the GoCarte API, developers should follow several best practices.

- Store API keys securely and avoid exposing them in client-side code  
- Monitor API rate limits to prevent request throttling  
- Validate API responses before processing application logic  
- Handle authentication errors and expired API keys appropriately  
- Implement application-side rate limiting to avoid exceeding GoCarte API usage limits  

---

# Next Steps

For detailed endpoint specifications, request parameters, and response formats, refer to the **GoCarte API Reference**.

Additional integration resources and developer tools are available through the **GoCarte developer portal**.
