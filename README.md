# Book Shop API Project

A complete RESTful API for a book shop with user authentication and async operations.

## Project Structure

```
book-shop-api/
├── index.js                 # Main server file
├── package.json            # Dependencies
├── client.js               # Axios client examples
└── router/
    ├── booksdb.js         # Books database
    ├── general.js         # Public routes
    └── auth_users.js      # Authenticated routes
```

## Installation Steps

### Step 1: Create Project Directory
```bash
mkdir book-shop-api
cd book-shop-api
```

### Step 2: Initialize Node.js Project
```bash
npm init -y
```

### Step 3: Install Dependencies
```bash
npm install express express-session jsonwebtoken axios
npm install --save-dev nodemon
```

### Step 4: Create Folder Structure
```bash
mkdir router
```

### Step 5: Create Files
Create the following files with the code provided:
- `index.js`
- `package.json`
- `client.js`
- `router/booksdb.js`
- `router/general.js`
- `router/auth_users.js`

### Step 6: Start the Server
```bash
npm start
```
Or for development with auto-reload:
```bash
npm run dev
```

The server will run on `http://localhost:5000`

## API Endpoints

### Public Routes (No Authentication Required)

#### Task 1: Get all books
```bash
GET http://localhost:5000/
```

#### Task 2: Get book by ISBN
```bash
GET http://localhost:5000/isbn/1
```

#### Task 3: Get books by Author
```bash
GET http://localhost:5000/author/Chinua%20Achebe
```

#### Task 4: Get books by Title
```bash
GET http://localhost:5000/title/Things%20Fall%20Apart
```

#### Task 5: Get book reviews
```bash
GET http://localhost:5000/review/1
```

#### Task 6: Register new user
```bash
POST http://localhost:5000/register
Content-Type: application/json

{
  "username": "testuser",
  "password": "password123"
}
```

### Authenticated Routes

#### Task 7: Login
```bash
POST http://localhost:5000/customer/login
Content-Type: application/json

{
  "username": "testuser",
  "password": "password123"
}
```

#### Task 8: Add/Modify review (authenticated)
```bash
PUT http://localhost:5000/customer/auth/review/1
Content-Type: application/json
Cookie: [session cookie from login]

{
  "review": "Great book! Highly recommended."
}
```

#### Task 9: Delete review (authenticated)
```bash
DELETE http://localhost:5000/customer/auth/review/1
Cookie: [session cookie from login]
```

### Async Routes (Tasks 10-13)

#### Task 10: Get all books (async)
```bash
GET http://localhost:5000/async/books
```

#### Task 11: Get book by ISBN (Promise)
```bash
GET http://localhost:5000/async/isbn/1
```

#### Task 12: Get books by Author (async)
```bash
GET http://localhost:5000/async/author/Chinua%20Achebe
```

#### Task 13: Get books by Title (async)
```bash
GET http://localhost:5000/async/title/Things%20Fall%20Apart
```

## Testing with Postman

1. **Register a user**: POST to `/register` with username and password
2. **Login**: POST to `/customer/login` to get session cookie
3. **Add review**: PUT to `/customer/auth/review/:isbn` (must be logged in)
4. **Delete review**: DELETE to `/customer/auth/review/:isbn` (must be logged in)

## Testing with Axios Client

Run the client examples:
```bash
# In client.js, uncomment the line: runExamples()
node client.js
```

## Task Completion Checklist

- ✅ Task 1: Get all books
- ✅ Task 2: Get book by ISBN
- ✅ Task 3: Get books by Author
- ✅ Task 4: Get books by Title
- ✅ Task 5: Get book reviews
- ✅ Task 6: Register new user
- ✅ Task 7: Login as registered user
- ✅ Task 8: Add/Modify review (authenticated)
- ✅ Task 9: Delete review (authenticated)
- ✅ Task 10: Get all books (async callback)
- ✅ Task 11: Search by ISBN (Promises)
- ✅ Task 12: Search by Author (async)
- ✅ Task 13: Search by Title (async)
- ⬜ Task 14: Submit GitHub link

## GitHub Submission

1. Initialize git repository:
```bash
git init
git add .
git commit -m "Initial commit: Book Shop API"
```

2. Create repository on GitHub

3. Push to GitHub:
```bash
git remote add origin <your-github-repo-url>
git branch -M main
git push -u origin main
```

## Notes

- Session-based authentication with JWT tokens
- All async operations include 1-second delay to simulate database operations
- Reviews are stored per user per book
- Users can only delete their own reviews

## Troubleshooting

**Port already in use:**
```bash
# Change PORT in index.js or kill process on port 5000
lsof -ti:5000 | xargs kill -9  # macOS/Linux
netstat -ano | findstr :5000   # Windows
```

**Module not found:**
```bash
npm install
```
