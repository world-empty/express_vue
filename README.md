# Express & Vue Full-Stack Application

![License](https://img.shields.io/badge/license-MIT-blue.svg)
![Node.js](https://img.shields.io/badge/Node.js-v18.x-green)
![Vue.js](https://img.shields.io/badge/Vue.js-3.x-4fc08d)
![Express.js](https://img.shields.io/badge/Express.js-404D59?logo=express)
[![Ask DeepWiki](https://devin.ai/assets/askdeepwiki.png)](https://deepwiki.com/world-empty/express_vue)

This repository contains a full-stack JavaScript application featuring an **Express.js** backend and a **Vue 3** frontend. The application demonstrates **user authentication** (registration and login) and **CRUD operations** (Create, Read, Update, Delete) for user management within a protected admin dashboard. It serves as a **starter template** for dashboards, admin panels, or projects requiring authentication and user management.

## 📌 Table of Contents

- [Project Structure](#project-structure)
- [Features](#features)
- [Tech Stack](#tech-stack)
- [Prerequisites](#prerequisites)
- [Installation and Setup](#installation-and-setup)
- [API Endpoints](#api-endpoints)
- [Usage](#usage)
- [Testing](#testing)
- [Contributing](#contributing)
- [License](#license)

## 🗂 Project Structure

The project is organized as a monorepo with two main directories:

```plaintext
express_vue/
├── backend-express/    # Node.js/Express REST API server
│   ├── prisma/         # Prisma schema and migrations
│   ├── routes/         # API routes
│   ├── controllers/    # Request handlers
│   ├── index.js        # Main backend entry point
│   └── ...
├── frontend-vue/       # Vue 3 single-page application (SPA)
│   ├── src/            # Vue components, services, and routes
│   │   ├── components/ # Reusable UI components
│   │   ├── views/      # Page views
│   │   ├── services/   # API service layer
│   ├── vite.config.js  # Vite configuration
│   └── ...
└── README.md
```

## ✨ Features

### Backend (Express.js)
- RESTful API for user authentication and management.
- JWT-based authentication using `jsonwebtoken`.
- Secure password hashing with `bcryptjs`.
- Input validation with `express-validator`.
- Database management with **Prisma ORM** (MySQL).
- Middleware for protecting authenticated routes.
- CORS enabled for seamless frontend communication.

### Frontend (Vue.js)
- Built with **Vue 3** (Composition API with `<script setup>`).
- Fast development with **Vite**.
- Client-side routing via `vue-router`.
- HTTP requests handled by `axios`.
- Token-based authentication with `js-cookie` for session management.
- Route guards to secure admin pages.
- Responsive UI styled with **Bootstrap 5**.
- Full CRUD functionality in the admin dashboard.

## 🛠 Tech Stack

- **Backend**: Node.js, Express.js, Prisma, MySQL, JSON Web Tokens (JWT), Bcrypt.js
- **Frontend**: Vue 3, Vite, Vue Router, Axios, JS-Cookie, Bootstrap 5
- **Database**: MySQL

## ⚙️ Prerequisites

Ensure the following are installed on your system:
- **Node.js** (v18.x or higher recommended)
- **npm** (Node Package Manager)
- **MySQL** database server (running and accessible)

## 🛠 Installation and Setup

Follow these steps to set up and run the application locally.

### 1. Clone the Repository
```bash
git clone https://github.com/world-empty/express_vue.git
cd express_vue
```

### 2. Backend Setup (`backend-express`)

1. **Navigate to the backend directory:**
   ```bash
   cd backend-express
   ```

2. **Install dependencies:**
   ```bash
   npm install
   ```

3. **Configure environment variables:**
   Copy the example `.env` file:
   ```bash
   cp .env.example .env
   ```
   Update the `.env` file with your MySQL connection details and a secure JWT secret:
   ```env
   DATABASE_URL="mysql://YOUR_USER:YOUR_PASSWORD@localhost:3306/db_express"
   JWT_SECRET=your-strong-jwt-secret
   ```
   Ensure the database `db_express` exists in your MySQL server.

4. **Run database migrations:**
   Apply the Prisma schema to your database:
   ```bash
   npx prisma migrate dev --name users
   ```

5. **Start the backend server:**
   The server will run on `http://localhost:3000`:
   ```bash
   node index.js
   ```

### 3. Frontend Setup (`frontend-vue`)

1. **Navigate to the frontend directory:**
   ```bash
   cd frontend-vue
   ```

2. **Install dependencies:**
   ```bash
   npm install
   ```

3. **Start the frontend development server:**
   The application will be available at `http://localhost:5173` (or another port if 5173 is occupied). The frontend is configured to communicate with the backend at `http://localhost:3000` via `src/services/api.js`.
   ```bash
   npm run dev
   ```

4. Open your browser to `http://localhost:5173` to access the application.

## 📡 API Endpoints

The backend exposes the following REST API endpoints under the `/api` prefix:

| Method | Endpoint                  | Description                       | Protected |
|--------|---------------------------|-----------------------------------|-----------|
| `POST` | `/api/register`           | Register a new user               | No        |
| `POST` | `/api/login`              | Log in and receive a JWT token    | No        |
| `GET`  | `/api/admin/users`        | List all users                    | Yes       |
| `POST` | `/api/admin/users`        | Create a new user                 | Yes       |
| `GET`  | `/api/admin/users/:id`    | Get a user by ID                  | Yes       |
| `PUT`  | `/api/admin/users/:id`    | Update a user by ID               | Yes       |
| `DELETE` | `/api/admin/users/:id`    | Delete a user by ID               | Yes       |

**Note**: Protected endpoints require a valid JWT token in the `Authorization` header (`Bearer <token>`).

## 🚀 Usage

1. **Register a User**: Navigate to the registration page (`/register`) and create an account.
2. **Log In**: Use the login page (`/login`) to authenticate and receive a JWT token.
3. **Access Admin Dashboard**: Log in with an authorized account to access the admin dashboard (`/admin`) for CRUD operations on users.
4. **Manage Users**: Use the admin dashboard to create, read, update, or delete user records.

## 🧪 Testing

To ensure the application works as expected, you can test the API and frontend manually or set up automated tests.

### Backend Testing
- Use tools like **Postman** or **curl** to test API endpoints.
- Example for registering a user:
  ```bash
  curl -X POST http://localhost:3000/api/register \
  -H "Content-Type: application/json" \
  -d '{"username":"testuser","password":"securepassword"}'
  ```

### Frontend Testing
- Verify frontend functionality by navigating through the UI.
- Test route guards by attempting to access `/admin` without a valid token.
- Automated tests can be added using **Vitest** or **Cypress** (not included in this repository).

## 🤝 Contributing

Contributions are welcome! To contribute:

1. Fork the repository.
2. Create a new branch (`git checkout -b feature/your-feature`).
3. Make your changes and commit (`git commit -m "Add your feature"`).
4. Push to the branch (`git push origin feature/your-feature`).
5. Open a pull request with a detailed description of your changes.

Please ensure your code follows the project's coding style and includes appropriate tests.

## 📄 License

This project is licensed under the [MIT License](LICENSE).

---

© 2025 world-empty
