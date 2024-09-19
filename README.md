# Task Management Application

## Overview

The **Task Management Application** is a full-stack project built using the **MERN** (MongoDB, Express, React, Node.js) stack. It allows users to manage tasks by creating, updating, deleting, and viewing tasks. The application includes user authentication and validation features to ensure secure task management.

## Features

- **User Authentication**: Secure registration and login functionality using JWT (JSON Web Tokens).
- **Task Management**: Users can create, update, delete, and view their tasks.
- **Validation**: User inputs are validated for correctness (e.g., strong passwords, valid email addresses).
- **Password Security**: Passwords are hashed using `bcryptjs` for added security.
- **Access Control**: Only authenticated users can manage their tasks.
- **Timestamps**: Tasks include `createdAt` and `updatedAt` timestamps for tracking.

## Tech Stack

### Backend:
- **Node.js**: JavaScript runtime for server-side logic.
- **Express.js**: Web framework for building RESTful APIs.
- **MongoDB**: NoSQL database for storing tasks and user data.
- **Mongoose**: MongoDB ORM for data modeling and validation.
- **JWT**: Token-based authentication for securing API routes.
- **bcryptjs**: For hashing passwords.

## Prerequisites

Ensure that the following are installed on your machine:
- **Node.js** (v14 or higher)
- **npm** (Node Package Manager)
- **MongoDB** (Local MongoDB instance or a MongoDB Atlas account)

## Installation and Setup

### Clone the Repository:
To start, clone the repository to your local machine:

git clone https://github.com/raju470/Task-Management-Backend.git

cd task-management

npm install

### In the root directory of the project, create a .env file with the following content
PORT=5000

MONGO_URI=mongodb+srv://<username>:<password>@<cluster-name>.mongodb.net/?retryWrites=true&w=majority

JWT_SECRET=yourSecretKey

JWT_EXPIRY=1h

### To start the application
npm start

## API Endpoints

#### Signup: POST /api/auth/register

Body:

    {
        "username": "user123",
        "email": "user@example.com",
        "password": "Password@123"
    }

Response:

    {
        "token": "<JWT_Token>"
    }

#### Login: POST /api/auth/login

Body:

    {
        "email": "user@example.com",
        "password": "Password123!"
    }

Response:

    {
        "token": "<JWT_Token>"
    }

#### Task Management
#### Create Task: POST /api/tasks
##### Set Authorization : "JWT_TOKEN" in header
Body:

    {
        "title": "Task Title",
        "description": "Task Description"
    }

Response:
  
    {
        "_id": "<Task_ID>",
        "title": "Task Title",
        "description": "Task Description",
        "user": "<User_ID>",
        "createdAt": "<Creation_Date>",
        "updatedAt": "<Update_Date>"
    }

### Update Task: PUT /api/tasks/:id
##### Set Authorization : "JWT_TOKEN" in header
Body:

    {
        "title": "Updated Task Title",
        "description": "Updated Task Description",
        "status": "completed"
    }

Response:

    {
        "_id": "<Task_ID>",
        "title": "Updated Task Title",
        "description": "Updated Task Description",
        "status": "completed",
        "user": "<User_ID>",
        "createdAt": "<Creation_Date>",
        "updatedAt": "<Update_Date>"
}

### Get All Tasks: GET /api/tasks
##### Set Authorization : "JWT_TOKEN" in header
    Response:
    [
     {
        "_id": "<Task_ID>",
        "title": "Task Title",
        "description": "Task Description",
        "user": "<User_ID>",
        "createdAt": "<Creation_Date>",
        "updatedAt": "<Update_Date>"
     }
    ]

### Get Task by ID: GET /api/tasks/:id
##### Set Authorization : "JWT_TOKEN" in header
Response:

    {
        "_id": "<Task_ID>",
        "title": "Task Title",
        "description": "Task Description",
        "user": "<User_ID>",
        "createdAt": "<Creation_Date>",
        "updatedAt": "<Update_Date>"
    }

### Delete Task: DELETE /api/tasks/:id
##### Set Authorization : "JWT_TOKEN" in header
Response:

    {
        "msg": "Task deleted successfully"
    }