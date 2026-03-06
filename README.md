# MongoDB Task - User CRUD API

A simple Node.js and Express application demonstrating CRUD (Create, Read, Update, Delete) operations with MongoDB using Mongoose.

## Features

- **User Management**: Create single or multiple users, fetch all users, or find a specific user by ID.
- **Updates**: Update user information using both `PUT` (full update) and `PATCH` (partial update for name).
- **Deletion**: Remove users from the database by ID.
- **Environment Driven**: Configuration via environment variables.

## Tech Stack

- **Node.js**
- **Express.js**
- **MongoDB** (via **Mongoose**)
- **CORS**
- **Dotenv**

## Getting Started

### Prerequisites

- Node.js installed
- MongoDB instance (local or Atlas)

### Installation

1. Clone the repository:
   ```bash
   git clone <repository-url>
   cd task
   ```

2. Install dependencies:
   ```bash
   npm install
   ```

3. Configure environment variables:
   Create a `.env` file in the root directory and add the following:
   ```env
   PORT=3000
   MongoDB_URI=your_mongodb_connection_string
   ```

### Running the Server

Start the server using:
```bash
npm start
```
The server will be running on the port specified in your `.env` file (defaulting to 3000).

## API Endpoints

| Method | Endpoint | Description |
| :--- | :--- | :--- |
| `GET` | `/` | Health check |
| `POST` | `/one` | Create a single user |
| `POST` | `/many` | Bulk create users |
| `GET` | `/users` | Get all users |
| `GET` | `/users/:id` | Get user by ID |
| `PUT` | `/users/:id` | Update user by ID |
| `PATCH` | `/users/name/:id` | Update user name by ID |
| `DELETE` | `/users/:id` | Delete user by ID |

## Schema

```javascript
{
  name: String,
  password: String
}
```

## Deploying to Render

### Option 1: Deploy with MongoDB Atlas

1. **Create a MongoDB Atlas cluster** (or use an existing one):
   - Sign up at [MongoDB Atlas](https://www.mongodb.com/atlas/database)
   - Create a free tier cluster
   - Create a database user with password
   - Add your IP to the IP access list (or allow 0.0.0.0/0 for all IPs)
   - Get your connection string

2. **Deploy to Render**:
   - Push your code to GitHub
   - Go to [Render Dashboard](https://dashboard.render.com)
   - Click "New +" and select "Web Service"
   - Connect your GitHub repository
   - Configure the following:
     - **Name**: your-app-name
     - **Runtime**: Node
     - **Build Command**: `npm install`
     - **Start Command**: `npm start`
   - Add environment variables:
     - `PORT`: `10000`
     - `MongoDB_URI`: your MongoDB Atlas connection string
   - Click "Create Web Service"

### Option 2: Deploy with Render's Managed Database

1. **Create a PostgreSQL database** on Render:
   - Go to [Render Dashboard](https://dashboard.render.com)
   - Click "New +" and select "Database"
   - Select "MongoDB" (if available) or use PostgreSQL
   - Follow the prompts to create the database

2. **Deploy the Web Service**:
   - Follow steps 2-6 from Option 1
   - Use the connection string from your Render database

### Important Notes

- Render assigns a random port via the `PORT` environment variable. Update your `.env` to use `PORT=${PORT}` or update your code to read from `process.env.PORT`.
- Ensure your MongoDB connection string includes the database name.
- For production, use environment variables on Render instead of a `.env` file.
