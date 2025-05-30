# Todo App v3 - Task Management API

## Overview

Todo App v3 is a comprehensive task management API that provides robust user authentication and task management capabilities. This backend API allows users to register, log in, create tasks, update their status, and manage their personal task lists securely.

## Features

- **User Authentication System**
  - Register new users with name, email, and password
  - Role-based access control (user/admin)
  - Secure login with JWT token authentication
  - User profile management

- **Task Management**
  - Create new tasks with title and description
  - List all tasks for the current user
  - View detailed task information  
  - Update task details and status
  - Delete tasks
  - Task ownership protection

## Technology Stack

- **Backend**: Node.js with Express.js
- **Database**: MongoDB (implied from the API structure)
- **Authentication**: JWT (JSON Web Tokens)
- **Testing**: Postman for API testing

## Getting Started

### Prerequisites

- Node.js (v12 or higher recommended)
- MongoDB installed and running
- Postman for testing the API

### Installation

1. Clone the repository:
   ```
   git clone https://github.com/yourusername/todo-app-v3.git
   cd todo-app-v3
   ```

2. Install dependencies:
   ```
   npm install
   ```

3. Create a `.env` file in the root directory with the following variables:
   ```
   PORT=5000
   MONGO_URI=your_mongodb_connection_string
   JWT_SECRET=your_jwt_secret_key
   ```

4. Start the server:
   ```
   npm start
   ```
   
   For development with auto-restart:
   ```
   npm run dev
   ```

## API Endpoints

### Authentication

| Method | Endpoint | Description | Auth Required |
|--------|----------|-------------|--------------|
| POST | `/api/auth/register` | Register a new user | No |
| POST | `/api/auth/login` | Log in and receive a token | No |
| GET | `/api/auth/me` | Get current user information | Yes |

### Task Management

| Method | Endpoint | Description | Auth Required |
|--------|----------|-------------|--------------|
| POST | `/api/tasks` | Create a new task | Yes |
| GET | `/api/tasks` | Get all tasks for current user | Yes |
| GET | `/api/tasks/:id` | Get a specific task by ID | Yes |
| PUT | `/api/tasks/:id` | Update a task | Yes |
| DELETE | `/api/tasks/:id` | Delete a task | Yes |

## Request & Response Examples

### Register User

**Request**:
```json
POST /api/auth/register
Content-Type: application/json

{
  "name": "John Doe",
  "email": "john.doe@example.com",
  "password": "Password123!",
  "role": "user"
}
```

**Success Response**:
```json
Status: 201 Created
{
  "user": {
    "_id": "60d21b4667d0d8992e610c85",
    "name": "John Doe",
    "email": "john.doe@example.com",
    "role": "user"
  },
  "token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9..."
}
```

### Create Task

**Request**:
```json
POST /api/tasks
Content-Type: application/json
Authorization: Bearer <your_token>

{
  "title": "Complete project documentation",
  "description": "Write comprehensive documentation for the API project including setup instructions and usage examples."
}
```

**Success Response**:
```json
Status: 201 Created
{
  "_id": "60d21b4667d0d8992e610c86",
  "title": "Complete project documentation",
  "description": "Write comprehensive documentation for the API project including setup instructions and usage examples.",
  "status": "pending",
  "user": "60d21b4667d0d8992e610c85",
  "createdAt": "2023-06-22T10:00:00.000Z",
  "updatedAt": "2023-06-22T10:00:00.000Z"
}
```

## Testing with Postman

The project includes a comprehensive Postman collection and environment for testing all API endpoints.

### Setup Instructions

1. Import the Postman collection JSON file into Postman
2. Import the Postman environment JSON file into Postman
3. Select the "Task API Environment" from the environment dropdown in Postman
4. Make sure your API server is running on http://localhost:5000 (or update the `baseUrl` environment variable)

### Testing Sequence

For the most effective testing, follow this sequence:

1. Register a user
2. Login with the user credentials
3. Create a task
4. Get all tasks
5. Get a specific task
6. Update a task
7. Delete a task

The Postman collection includes automated scripts that will:
- Save authentication tokens automatically when logging in
- Save task IDs automatically when creating tasks

## Error Handling

The API includes comprehensive error handling for various scenarios:

- Invalid authentication attempts
- Missing required fields
- Invalid data formats
- Accessing non-existent resources
- Unauthorized access to resources

## Security Features

- Passwords are hashed before storage
- JWT tokens are used for authentication
- Route protection middleware for authenticated endpoints
- Role-based access control
- Task ownership verification

## Contributing

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add some amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

## License

This project is licensed under the MIT License.

## Contact

 Tel:
 email:
 linkedIn:
 github repo:
---
