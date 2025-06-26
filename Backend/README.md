# Task Management App Backend

This is the backend for a task management application, providing a RESTful API for user authentication and task management. It is built with **Node.js**, **Express.js**, and **MongoDB**.

## Features
- User registration and login with JWT authentication
- Secure password hashing with bcryptjs
- CRUD operations for tasks (create, read, update, delete)
- Protected task routes (require authentication)
- CORS enabled for frontend-backend communication

## Tech Stack
- Node.js
- Express.js
- MongoDB & Mongoose
- JWT for authentication
- bcryptjs for password hashing
- dotenv for environment variables
- CORS

## Getting Started

### Prerequisites
- Node.js (v16 or higher recommended)
- npm
- MongoDB database (local or Atlas)

### Installation
1. Clone the repository:
   ```sh
   git clone <YOUR_REPO_URL>
   cd Backend
   ```
2. Install dependencies:
   ```sh
   npm install
   ```
3. Create a `.env` file in the `Backend` directory with the following content:
   ```env
   MONGO_URI=your_mongodb_connection_string
   JWT_SECRET=your_jwt_secret_here
   PORT=5000
   ```
4. Start the server:
   ```sh
   node server.js
   ```
   The server will run on `http://localhost:5000` by default.

## API Endpoints

### Auth
- `POST /api/auth/signup` — Register new user
  - Body: `{ username, email, password }`
- `POST /api/auth/login` — Login user, returns JWT
  - Body: `{ email, password }`

### Tasks (Protected by JWT)
- `GET /api/tasks` — Get all tasks for logged-in user
- `POST /api/tasks` — Create new task
- `PUT /api/tasks/:id` — Update task
- `DELETE /api/tasks/:id` — Delete task

All task routes require the `Authorization: Bearer <token>` header.

## Environment Variables
- `MONGO_URI` — MongoDB connection string
- `JWT_SECRET` — Secret for JWT signing
- `PORT` — Server port (default: 5000)

## Folder Structure
```
Backend/
  models/
    user.js
    task.js
  routes/
    auth.js
    tasks.js
  middleware/
    auth.js
  server.js
  .env
  package.json
```

## Notes
- Passwords are hashed using bcryptjs.
- All task routes are protected and require a valid JWT.
- CORS is enabled for frontend-backend communication.

## Related Frontend
The frontend for this project is located in `frontend/agile-task-master-board/` and is built with React, Vite, TypeScript, shadcn-ui, and Tailwind CSS.

---
For more details, see the [DESIGN.md](./DESIGN.md) file. 