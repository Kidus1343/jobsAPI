# Jobs API

A RESTful API built with **Node.js**, **Express**, and **MongoDB** to manage job listings for authenticated users. It features user registration, login, and full CRUD operations for job postings using **JWT** authentication and **Mongoose**.

---

### 🚀 Features

- **User Authentication**
  - Register and log in using JWT-based authentication
  - Password hashing with bcrypt

- **Job Management**
  - Create, read, update, and delete job listings
  - Fields: `company`, `position`, `status` (interview, declined, pending)
  - Jobs are tied to authenticated users and sorted by creation date

- **Custom Error Handling**
  - Structured responses for validation, unauthorized access, not found, and MongoDB errors

- **MongoDB Integration**
  - Persistent storage with Mongoose schemas

- **Middleware**
  - JWT Authentication middleware
  - Global error handling

---

### 📦 Prerequisites

- Node.js (v14 or higher)
- MongoDB (local or cloud e.g., Atlas)
- npm (Node Package Manager)

---

### 🛠️ Installation

```bash
git clone https://github.com/Kidus1343/jobsAPI.git
cd jobsAPI
npm install
⚙️ Environment Variables
Create a .env file in the root with the following:

ini
Copy
Edit
PORT=3000
MONGO_URI=your_mongodb_connection_string
JWT_SECRET=your_jwt_secret_key
JWT_LIFETIME=30d

▶️ Run the Application
bash
Copy
Edit
npm start
Visit the API on: http://localhost:3000

📌 API Endpoints
All job routes require a valid JWT in the Authorization header (Bearer <token>)

🔐 Authentication
POST /api/v1/auth/register
Register a new user.

Request:

json
Copy
Edit
{
  "name": "John Doe",
  "email": "john@example.com",
  "password": "secret123"
}
Response:

json
Copy
Edit
{
  "user": { "name": "John Doe" },
  "token": "..."
}
POST /api/v1/auth/login
Login existing user.

Request:

json
Copy
Edit
{
  "email": "john@example.com",
  "password": "secret123"
}
Response:

json
Copy
Edit
{
  "user": { "name": "John Doe" },
  "token": "..."
}
📄 Jobs
GET /api/v1/jobs
Get all jobs created by the authenticated user.

Response:

json
Copy
Edit
{
  "jobs": [ ... ],
  "count": 2
}
GET /api/v1/jobs/:id
Get a specific job by ID.

Response:

json
Copy
Edit
{
  "job": {
    "company": "Tech Corp",
    "position": "Developer",
    ...
  }
}
POST /api/v1/jobs
Create a new job.

Request:

json
Copy
Edit
{
  "company": "Tech Corp",
  "position": "Developer",
  "status": "interview"
}
Response: 201 Created

PATCH /api/v1/jobs/:id
Update a job.

Request:

json
Copy
Edit
{
  "company": "New Corp",
  "position": "Senior Developer",
  "status": "pending"
}
DELETE /api/v1/jobs/:id
Delete a specific job.

Response: 200 OK

❌ Error Handling
400 Bad Request: Invalid or missing data

401 Unauthorized: Invalid/missing token or credentials

404 Not Found: Job not found or not owned by user

MongoDB Specific:

Validation errors

Duplicate email on registration

CastError on invalid IDs

📁 Project Structure
pgsql
Copy
Edit
├── controllers/
│   ├── auth.js
│   └── jobs.js
├── db/
│   └── connect.js
├── errors/
│   ├── bad-request.js
│   ├── not-found.js
│   ├── unauthenticated.js
│   └── index.js
├── middleware/
│   ├── auth.js
│   └── error-handler.js
├── models/
│   ├── Job.js
│   └── User.js
├── routes/
│   ├── auth.js
│   └── jobs.js
⚙️ Configuration
Key	Description
PORT	App port (default: 3000)
MONGO_URI	MongoDB connection string
JWT_SECRET	Secret key for signing JWTs
JWT_LIFETIME	Token expiry duration (e.g., 30d)

📚 Dependencies
express: Node.js framework

mongoose: MongoDB ORM

jsonwebtoken: JWT handling

bcryptjs: Password hashing

http-status-codes: HTTP status constants

Check package.json for the full list.

🤝 Contributing
Fork the repo

Create your feature branch: git checkout -b feature/my-feature

Commit changes: git commit -m "Add my feature"

Push: git push origin feature/my-feature

Open a pull request 🚀
