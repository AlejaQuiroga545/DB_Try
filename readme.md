# Library Management System

This is a monolithic system for managing a library, allowing you to handle users, books, and loans. The backend is built with Node.js and Express, the database is managed with MySQL, and the frontend is located within the app folder.

---

## Technologies used

Node.js
Express.js
MySQL
HTML, CSS, JavaScript (Frontend)
csv-parser (to load data from CSV files)
vite

---

## Project Structure

```bash
biblioteca/
│
├── docs/ # Documentation
│       ...
├── app/ # Frontend (HTML, CSS, JS)
│       ...
├── server/ # Backend
│       ...
├── index.html 
├── .env # Environment variables
├── .gitignore
└── README.md
```

## Installation


1. Clone the repository:

```bash
git clone https://github.com/jcomte23/biblioteca-easy.git
cd biblioteca
```
2. Install dependencies:

```bash
npm install
```

3. Create and configure the .env file:

```bash
DB_HOST=localhost
DB_USER=root
DB_PASSWORD=password
DB_NAME=db_name
DB_PORT=3306
```

4. Initialize the backend::
```bash
node server/index.js
```

5. Initialize the frontend:
```bash
npm run dev
```

# License
This project is under the MIT license. You are free to use, modify, and distribute it.
