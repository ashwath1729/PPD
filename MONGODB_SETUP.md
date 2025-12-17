# MongoDB Setup Instructions

The backend requires MongoDB to be running. Choose one of the following options:

## Option 1: Local MongoDB (Recommended for Development)

### Install MongoDB Community Edition
1. Download from: https://www.mongodb.com/try/download/community
2. Run the installer
3. Choose "Complete" installation
4. Select "Install MongoDB as a Service"

### Start MongoDB Service
```bash
# Windows
net start MongoDB

# Or if not installed as service
mongod --dbpath="C:\data\db"
```

## Option 2: MongoDB Atlas (Cloud - Free Tier)

### Setup Atlas
1. Go to https://www.mongodb.com/cloud/atlas
2. Create a free account
3. Create a new cluster (M0 Free tier)
4. Create a database user
5. Add IP whitelist (0.0.0.0/0 for development)
6. Get connection string

### Update .env
```env
MONGODB_URI=mongodb+srv://<username>:<password>@cluster0.xxxxx.mongodb.net/productivity-dashboard?retryWrites=true&w=majority
```

## Option 3: Docker MongoDB

```bash
docker run -d -p 27017:27017 --name mongodb mongo:latest
```

## Verify Connection

```bash
# Test MongoDB connection
mongosh

# Or with connection string
mongosh mongodb://localhost:27017
```

## Current Status

⚠️ **MongoDB is not running on your system**

The backend server is trying to connect to:
```
mongodb://localhost:27017/productivity-dashboard
```

**Error**: `ECONNREFUSED`

### Quick Fix

Choose **Option 2 (MongoDB Atlas)** for fastest setup:
1. Create free Atlas account
2. Get connection string
3. Update `server/.env` with Atlas connection string
4. Restart backend server

### Or Install Locally

1. Download MongoDB Community: https://www.mongodb.com/try/download/community
2. Run installer with default settings
3. Start MongoDB service:
   ```bash
   net start MongoDB
   ```
4. Restart backend server

## Backend Status

- ✅ Backend server code ready
- ✅ All routes and controllers implemented
- ❌ MongoDB connection needed
- 🔄 Waiting for database connection

Once MongoDB is running, restart the backend:
```bash
cd server
node index.js
```

You should see:
```
MongoDB Connected: localhost
Server running in development mode on port 4000
```
