# Cruds
A full-stack CRUD application built with React.js (Vite) for the frontend, Node.js and Express.js for the backend, and MySQL for data storage. All users can view books without login, while only authenticated users can log in to create, update, or delete books.
# MySQL Database
Database Name: booksdb
Tables: users, books
# books table description
id, title, author, year

# users table description
id, username, email, password

# Database
CREATE DATABASE IF NOT EXISTS booksdb;
USE booksdb;

-- users table
CREATE TABLE IF NOT EXISTS users (
  id INT AUTO_INCREMENT PRIMARY KEY,
  username VARCHAR(100) NOT NULL,
  email VARCHAR(255) NOT NULL UNIQUE,
  password VARCHAR(255) NOT NULL,
  created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

-- books table
CREATE TABLE IF NOT EXISTS books (
  id INT AUTO_INCREMENT PRIMARY KEY,
  title VARCHAR(255) NOT NULL,
  author VARCHAR(255) NOT NULL,
  year INT,
  created_by INT, -- FK to user who created it (optional)
  created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
  FOREIGN KEY (created_by) REFERENCES users(id) ON DELETE SET NULL
);


# Run frontend
cd frontend
npm install
npm run dev

# Run backend
cd backend
npm install
node index.js
