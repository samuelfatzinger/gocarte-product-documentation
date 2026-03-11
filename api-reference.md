# GoCarte API Reference

## Overview

The GoCarte API allows developers to interact with GoCarte projects and tasks programmatically. Using the API, applications can create projects, manage tasks, and retrieve project information in a GoCarte Workroom.

The GoCarte API follows standard REST principles and returns responses in JSON format.

---

## Base URL

All API requests use the following base URL:

```
https://api.gocarte.com/v1
```

All endpoints described in this guide are relative to this base URL.

---

## Authentication

The GoCarte API uses **API key authentication**.

Each request must include an API key in the **Authorization header**.

Example:

```
Authorization: Bearer YOUR_API_KEY
```

If the API key is missing or invalid, the request returns a **401 Unauthorized** response.

---

## Common Response Codes

The GoCarte API returns standard HTTP status codes.

| Status Code | Meaning |
|-------------|--------|
| 200 | Request successful |
| 201 | Resource created |
| 400 | Bad request |
| 401 | Unauthorized |
| 403 | Forbidden |
| 404 | Resource not found |
| 429 | Too many requests |
| 500 | Internal server error |

---

# Projects Endpoint

## Get All Projects

Returns a list of projects within the authenticated Workroom.

**Request**

```
GET /projects
```

**Example Request**

```
GET https://api.gocarte.com/v1/projects
```

**Example Response**

```json
{
  "projects": [
    {
      "id": "prj_1042",
      "name": "Website Redesign",
      "status": "active"
    },
    {
      "id": "prj_1043",
      "name": "Marketing Campaign",
      "status": "active"
    }
  ]
}
```

---

## Create a Project

Creates a new project in the authenticated Workroom.

**Request**

```
POST /projects
```

### Parameters

| Parameter | Type | Description |
|-----------|------|-------------|
| name | string | Name of the project |
| description | string | Short description of the project |

### Request Body

```json
{
  "name": "Product Launch",
  "description": "Planning tasks for upcoming release"
}
```

**Response**

```
201 Created
```

---

# Tasks Endpoint

## Get Tasks for a Project

Returns all tasks associated with the specified project.

**Request**

```
GET /projects/{project_id}/tasks
```

### Parameters

| Parameter | Type | Description |
|-----------|------|-------------|
| project_id | string | Unique identifier for the project |

**Example**

```
GET /projects/prj_1042/tasks
```

**Response**

```
200 OK
```

---

## Create a Task

Creates a new task within a project.

**Request**

```
POST /tasks
```

### Parameters

| Parameter | Type | Description |
|-----------|------|-------------|
| project_id | string | Project where the task will be created |
| title | string | Title of the task |
| assigned_to | string | User assigned to the task |
| due_date | date | Task due date |

### Request Body

```json
{
  "project_id": "prj_1042",
  "title": "Design landing page",
  "assigned_to": "user_301",
  "due_date": "2025-05-15"
}
```

**Response**

```
201 Created
```

---

## Update Task Status

Updates the status of an existing task.

**Request**

```
PATCH /tasks/{task_id}
```

### Parameters

| Parameter | Type | Description |
|-----------|------|-------------|
| task_id | string | Unique identifier for the task |

### Request Body

```json
{
  "status": "In Progress"
}
```

**Response**

```
200 OK
```

---

## Error Handling

If a request fails, the GoCarte API returns an HTTP status code and an error message in the response body.

**Example Error Response**

```json
{
  "error": "Unauthorized request. API key is invalid."
}
```

Common errors include:

- **401 Unauthorized**
- **403 Forbidden**
- **404 Not Found**

---

## Rate Limits

To ensure service stability, API requests are limited to **100 requests per minute per API key**.

Requests that exceed this limit return a:

```
429 Too Many Requests
```

response.

---

## Next Steps

For implementation guidance, refer to the **GoCarte Developer Guide**, which provides examples of integrating GoCarte with external applications.
