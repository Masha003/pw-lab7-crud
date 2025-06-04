# Blog Posts CRUD API

A RESTful API built with Node.js and Express that provides authentication and CRUD operations for blog posts.

## Features

- User authentication (signup, signin, signout)
- JWT-based authorization
- CRUD operations for blog posts
- Input validation using Joi
- Password hashing with bcrypt
- MongoDB integration
- Security features with Helmet
- CORS support

## Prerequisites

- Node.js (v18 or higher)
- MongoDB Atlas account
- npm or yarn package manager

## Installation

1. Clone the repository
2. Install dependencies:

```bash
npm install
```

3. Create a `.env` file in the root directory with the following variables:

```properties
PORT=8000
MONGO_URI=your_mongodb_connection_string
TOKEN_SECRET=your_jwt_secret
NODE_CODE_SENDING_EMAIL_ADDRESS=your_email_address
```

## Running the Application

Development mode with auto-reload:

```bash
npm run dev
```

Production mode:

```bash
npm start
```

## API Endpoints

### Authentication

- `POST /api/auth/signup` - Register a new user
- `POST /api/auth/signin` - Login user
- `POST /api/auth/signout` - Logout user

### Posts

- `GET /api/posts/all-posts` - Get all posts (paginated)
- `GET /api/posts/single-post` - Get a single post by ID
- `POST /api/posts/create-post` - Create a new post
- `PUT /api/posts/update-post` - Update an existing post
- `DELETE /api/posts/delete-post` - Delete a post

## Authentication

The API uses JWT tokens for authentication. Protected routes require a valid JWT token which should be included in:

- Browser requests: Sent automatically via HTTP-only cookie
- Non-browser requests: Include in Authorization header as `Bearer <token>`

## Data Models

### User Schema

- email (String, required, unique)
- password (String, required)
- verified (Boolean)
- timestamps

### Post Schema

- title (String, required)
- description (String, required)
- userId (ObjectId, reference to User)
- timestamps

## Security Features

- Password hashing using bcrypt
- HTTP-only cookies for JWT storage
- Helmet middleware for security headers
- Input validation and sanitization
- CORS protection

## Error Handling

The API implements proper error handling with appropriate HTTP status codes and error messages for:

- Invalid input data
- Authentication errors
- Authorization errors
- Resource not found
- Server errors
