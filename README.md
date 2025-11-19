# LabTrack Library Management System

A full-stack MERN (MongoDB, Express.js, React, Node.js) application designed to manage library operations, including book cataloging, user management, book requests, issues, and returns. It features an intuitive user interface for clients and a comprehensive admin panel for library staff.

## ✨ Features

*   **User Authentication**: Secure login and signup for both regular users and administrators.
*   **Book Catalog**: Browse, search, and filter a wide range of books.
*   **Book Transactions**: Users can request books, and administrators can approve, issue, and manage returns.
*   **Real-time Notifications**: Socket.IO for instant updates on book request statuses.
*   **Caching**: Redis integration for improved API response times (e.g., popular books, categories).
*   **Admin Panel**: Dedicated interface for managing books, users, and transactions.
*   **Book Recommendations**: Content-based filtering to suggest books to users.
*   **Responsive Design**: Built with React and styled for a seamless experience across devices.

## 🚀 Tech Stack

*   **Frontend**: React.js, React Router DOM, Axios, Socket.IO Client
*   **Backend**: Node.js, Express.js, MongoDB (Mongoose), JSON Web Tokens (JWT), Redis, Socket.IO, Multer (for file uploads)
*   **Database**: MongoDB
*   **Caching**: Redis

## 🛠️ Getting Started

Follow these instructions to get a copy of the project up and running on your local machine for development and testing purposes.

### Prerequisites

Before you begin, ensure you have the following installed:

*   **Node.js & npm**: [Download Node.js](https://nodejs.org/en/download/) (npm is included with Node.js)
*   **MongoDB**: [Install MongoDB Community Edition](https://docs.mongodb.com/manual/installation/)
*   **Redis**: [Install Redis](https://redis.io/docs/getting-started/installation/) (e.g., `brew install redis` on macOS)
    *   Ensure Redis is running (e.g., `brew services start redis` on macOS).

### Installation

1.  **Clone the repository**:
    ```bash
    git clone <repository_url>
    cd LibraryManagementSystem
    ```

2.  **Backend Setup**:
    ```bash
    cd backend
    npm install
    ```
    *   **Environment Variables**: Create a `.env` file in the `backend` directory. Copy the contents from `info/BackendInfo/EnvVariables.txt` and fill in your `CONNECTION_URL`, `JWT_SECRET`, and `REDIS_URL`.
        *   For local Redis, set `REDIS_URL=redis://127.0.0.1:6379`.
    ```bash
    # Example .env content (fill in your actual values)
    CONNECTION_URL=mongodb://localhost:27017/librarymgmtsystem
    JWT_SECRET=your_jwt_secret_key
    REDIS_URL=redis://127.0.0.1:6379
    # ... other variables from info/BackendInfo/EnvVariables.txt
    ```

3.  **Frontend Setup**:
    ```bash
    cd ../frontend
    npm install
    ```

### Database Setup

You need to import the sample data into your MongoDB database. Ensure your MongoDB server is running.

From the project root directory (`LibraryManagementSystem/`), run the following commands:

```bash
# Replace 'librarymgmtsystem' with your actual database name if different
mongosh librarymgmtsystem --eval 'db.userdetails.insertMany(JSON.parse(cat("info/mongoDatabase/userdetails.json")))'
mongosh librarymgmtsystem --eval 'db.bookslists.insertMany(JSON.parse(cat("info/mongoDatabase/bookslists.json")))'
mongosh librarymgmtsystem --eval 'db.popularbooks.insertMany(JSON.parse(cat("info/mongoDatabase/popularbooks.json")))'
mongosh librarymgmtsystem --eval 'db.useremailverifications.insertMany(JSON.parse(cat("info/mongoDatabase/useremailverifications.json")))'
```
*Note: If `mongosh` is not found, you might need to use `mongoimport` or ensure `mongosh` is in your system's PATH.*

## 🏃 Running the Application

1.  **Start the Backend Server**:
    In the `backend` directory:
    ```bash
    npm run dev
    ```
    The backend will run on `http://localhost:5000`.

2.  **Start the Frontend Development Server**:
    In a new terminal, in the `frontend` directory:
    ```bash
    npm run dev
    ```
    The frontend will run on `http://localhost:5173`.

Open your browser and navigate to `http://localhost:5173` to access the application.

## 🔑 Login Credentials

*   **Admin User**:
    *   **Email**: `admin@gmail.com`
    *   **Password**: `admin`
*   **Client User**: You can create a new user account via the signup page.

## 📂 Folder Structure

```
.
├── backend/                  # Backend (Node.js/Express)
│   ├── controller/           # Business logic for API endpoints
│   ├── database/             # MongoDB and Redis connection setup
│   ├── errorHandler/         # Custom error handling
│   ├── middleware/           # Authentication, caching, etc.
│   ├── models/               # Mongoose schemas
│   ├── routes/               # API route definitions
│   ├── uploads/              # Book image uploads
│   └── app.js                # Main backend application file
├── frontend/                 # Frontend (React.js)
│   ├── public/               # Static assets
│   └── src/                  # React source code
│       ├── ADMIN/            # Admin specific components and pages
│       └── CLIENT/           # Client specific components and pages
├── info/                     # Project documentation and sample data
│   ├── BackendInfo/          # Backend specific info (e.g., EnvVariables.txt)
│   ├── mongoDatabase/        # Sample JSON data for MongoDB
│   └── postmanCollection/    # Postman collection for API testing
└── README.md                 # This file
```

## 🤝 Contributing

Contributions are welcome! Please feel free to submit a pull request or open an issue.

## 📄 License

This project is licensed under the MIT License - see the LICENSE.md file for details.
