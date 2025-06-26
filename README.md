# Task Management App

A full-stack task management application with a modern React frontend and a secure Node.js/Express backend. This project allows users to register, log in, and manage their tasks with a clean UI and robust API.

---

## Project Structure

```
.
├── Backend/   # Node.js, Express, MongoDB API
└── frontend/
    └── agile-task-master-board/   # React, Vite, TypeScript, Tailwind CSS UI
```

---

## Tech Stack

### Backend
- Node.js
- Express.js
- MongoDB & Mongoose
- JWT for authentication
- bcryptjs for password hashing
- dotenv for environment variables
- CORS

### Frontend
- React
- Vite
- TypeScript
- Tailwind CSS
- shadcn-ui

---

## Getting Started

### Prerequisites
- Node.js (v16 or higher recommended)
- npm
- MongoDB database (local or Atlas)

### Backend Setup
1. Navigate to the backend directory:
   ```sh
   cd Backend
   ```
2. Install dependencies:
   ```sh
   npm install
   ```
3. Create a `.env` file in the `Backend` directory:
   ```env
   MONGO_URI=your_mongodb_connection_string
   JWT_SECRET=your_jwt_secret_here
   PORT=5000
   ```
4. Start the backend server:
   ```sh
   node server.js
   ```
   The backend will run on `http://localhost:5000` by default.

### Frontend Setup
1. Navigate to the frontend directory:
   ```sh
   cd frontend/agile-task-master-board
   ```
2. Install dependencies:
   ```sh
   npm install
   ```
3. Start the frontend development server:
   ```sh
   npm run dev
   ```
   The frontend will run on `http://localhost:5173` by default (see terminal output).

---

## Features
- User registration and login (JWT authentication)
- Secure password storage
- CRUD operations for tasks
- Responsive, modern UI
- Protected API routes
- CORS enabled for frontend-backend communication

---

## API Overview

The backend exposes RESTful endpoints for authentication and task management. See `Backend/README.md` for full details.

---

## Folder Details

- **Backend/**: Express API, MongoDB models, authentication, and task routes
- **frontend/agile-task-master-board/**: React app, UI components, state management

---

## More Information
- Backend details: [Backend/README.md](Backend/README.md)
- Frontend details: [frontend/agile-task-master-board/README.md](frontend/agile-task-master-board/README.md)
- Backend design: [Backend/DESIGN.md](Backend/DESIGN.md)

---

## License
This project is licensed under the ISC License. 