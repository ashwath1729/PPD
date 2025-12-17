# Personal Productivity Dashboard

A full-stack MERN (MongoDB, Express, React, Node.js) Personal Productivity Dashboard with JWT authentication, task management, and analytics.

## Features

### 🔐 Authentication
- User registration and login with JWT tokens
- Bcrypt password hashing
- Protected routes and middleware
- Token-based session management

### ✅ Task Management
- Create, read, update, and delete tasks
- Date-based task organization
- **Business Rule**: Only today's tasks can be marked complete
- **Immutable Past Tasks**: Past tasks are read-only
- Filter tasks by date, week, month, and completion status

### 📊 Analytics Dashboard
- Daily task completion statistics
- Weekly progress with daily breakdown
- Monthly completion percentage
- Interactive Chart.js visualizations (Line, Bar, Doughnut)
- Productivity trends over time

### 🎨 UI/UX
- Minimal black and white theme
- Responsive Tailwind CSS design
- Fixed sidebar navigation
- Loading skeletons
- Error handling and validation

## Tech Stack

### Frontend
- **React 19** - UI library
- **React Router 6** - Client-side routing
- **Vite** - Build tool and dev server
- **Tailwind CSS** - Utility-first styling
- **Chart.js** - Data visualization
- **Axios** - HTTP client

### Backend
- **Node.js** - JavaScript runtime
- **Express.js** - Web framework
- **MongoDB** - NoSQL database
- **Mongoose** - ODM for MongoDB
- **JWT** - Authentication tokens
- **bcryptjs** - Password hashing
- **express-validator** - Input validation

## Getting Started

### Prerequisites
- Node.js 16+ installed
- MongoDB installed and running

### Installation

#### 1. Setup Backend
```bash
cd server
npm install

# Create .env file
cp .env.example .env
# Edit .env with your MongoDB URI and JWT secret
```

#### 2. Setup Frontend
```bash
cd ..  # Back to root
npm install

# Create .env file
cp .env.example .env
```

### Running the Application

#### 1. Start MongoDB
```bash
# Windows (if installed as service)
net start MongoDB
```

#### 2. Start Backend Server
```bash
cd server
node index.js
# Server runs on http://localhost:4000
```

#### 3. Start Frontend
```bash
# In root directory
npm run dev
# Frontend runs on http://localhost:5173
```

#### 4. Open Browser
Navigate to **http://localhost:5173**

## API Endpoints

### Authentication
```
POST   /api/auth/register    # Register new user
POST   /api/auth/login       # Login user
GET    /api/auth/me          # Get current user
```

### Tasks
```
GET    /api/tasks            # Get all tasks
POST   /api/tasks            # Create task
PATCH  /api/tasks/:id/toggle # Toggle completion (today only)
DELETE /api/tasks/:id        # Delete task
```

### Analytics
```
GET    /api/analytics/daily      # Daily statistics
GET    /api/analytics/weekly     # Weekly progress
GET    /api/analytics/monthly    # Monthly analytics
```

## Business Rules

- ✅ Can create tasks for today or future dates
- ❌ Cannot create tasks for past dates
- ✅ Can toggle completion for **today's tasks only**
- ❌ Past tasks are **read-only**

## Documentation

- **Backend API**: [server/API_DOCUMENTATION.md](./server/API_DOCUMENTATION.md)
- **Database Schema**: [server/SCHEMA_DOCUMENTATION.md](./server/SCHEMA_DOCUMENTATION.md)

## License

MIT
