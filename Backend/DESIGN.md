# Backend Design Document: Task Management App

## System Architecture

```
[ React Frontend ]  <--->  [ Express.js API Server ]  <--->  [ MongoDB Database ]
        |                           |                              |
   (React Router,           (RESTful Endpoints,              (Task & User
    Gantt/Kanban UI)         JWT Auth, CRUD)                  Collections)
```

## Database Schema

### User Schema
- `_id` (ObjectId)
- `username` (String, unique, required)
- `email` (String, unique, required)
- `password` (String, hashed, required)
- `createdAt`, `updatedAt` (Date, auto)

### Task Schema
- `_id` (ObjectId)
- `title` (String, required)
- `description` (String)
- `status` (String: "todo", "in-progress", "done"; default: "todo")
- `startDate` (Date, required)
- `endDate` (Date, required)
- `user` (ObjectId, ref: User, required)
- `createdAt`, `updatedAt` (Date, auto)

## API Endpoints

### Auth
- `POST /api/auth/signup` — Register new user
  - Body: `{ username, email, password }`
  - Response: `{ message }`

- `POST /api/auth/login` — Login user, returns JWT
  - Body: `{ email, password }`
  - Response: `{ token, user }`

### Tasks (Protected by JWT)
- `GET /api/tasks` — Get all tasks for logged-in user
  - Header: `Authorization: Bearer <token>`
  - Response: `[ { task }, ... ]`

- `POST /api/tasks` — Create new task
  - Header: `Authorization: Bearer <token>`
  - Body: `{ title, description, status, startDate, endDate }`
  - Response: `{ task }`

- `PUT /api/tasks/:id` — Update task
  - Header: `Authorization: Bearer <token>`
  - Body: `{ ...fields to update }`
  - Response: `{ task }`

- `DELETE /api/tasks/:id` — Delete task
  - Header: `Authorization: Bearer <token>`
  - Response: `{ message }`

## Environment Variables (.env)
- `MONGO_URI` — MongoDB connection string
- `JWT_SECRET` — Secret for JWT signing
- `PORT` — Server port (default: 5000)

## Middleware
- `auth.js`: JWT authentication middleware to protect task routes.

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