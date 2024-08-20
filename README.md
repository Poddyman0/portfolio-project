# Northcoders News API Project

## Project Description

In this project, I developed a RESTful API designed to serve as the backend for a news application. The API allows for the retrieval, creation, updating, and deletion of news articles, comments, and users, emulating the functionality of a real-world service like Reddit. This project involved using PostgreSQL for data storage and interacting with it through the `node-postgres` library. The API provides a robust and flexible way to manage and access news data programmatically.

## Technologies Used

- **Node.js:** Served as the runtime environment for the server-side application.
- **Express.js:** Used to build the RESTful API, manage routing, and handle HTTP requests.
- **PostgreSQL:** Implemented as the relational database management system for storing and querying data.
- **node-postgres:** Utilized for interfacing with the PostgreSQL database from Node.js.
- **Husky:** Employed to enforce code quality through pre-commit hooks that ensure tests pass before code is committed.

## Features

### Endpoints

1. **GET /api/topics**
   - Returns a list of topics available in the news database.
   - **Response Example:**
     ```json
     [
       {
         "slug": "technology",
         "description": "All about the latest in technology."
       },
       {
         "slug": "sports",
         "description": "News on sports events and updates."
       }
     ]
     ```

2. **GET /api**
   - Provides a list of available API endpoints.
   - **Response Example:**
     ```json
     {
       "GET /api/topics": "Returns a list of topics",
       "GET /api/articles/:article_id": "Returns an article by ID",
       "GET /api/articles": "Returns a list of all articles",
       "GET /api/articles/:article_id/comments": "Returns comments for a specific article",
       "POST /api/articles/:article_id/comments": "Adds a comment to a specific article",
       "PATCH /api/articles/:article_id": "Updates details of an article",
       "DELETE /api/comments/:comment_id": "Deletes a comment"
     }
     ```

3. **GET /api/articles/:article_id**
   - Retrieves a single article by its ID.
   - **Response Example:**
     ```json
     {
       "article_id": 1,
       "title": "The Rise of Technology",
       "body": "An in-depth look at how technology is changing our world.",
       "votes": 100,
       "created_at": "2023-08-20T00:00:00.000Z",
       "topic": "technology",
       "author": "John Doe"
     }
     ```

4. **GET /api/articles**
   - Fetches a list of all articles with support for filtering and sorting via query parameters.
   - **Query Parameters:**
     - `sort_by`: Field to sort by (e.g., `created_at`, `votes`).
     - `order`: Sort order (`asc` or `desc`).
     - `topic`: Filter by topic.
   - **Response Example:**
     ```json
     [
       {
         "article_id": 1,
         "title": "The Rise of Technology",
         "body": "An in-depth look at how technology is changing our world.",
         "votes": 100,
         "created_at": "2023-08-20T00:00:00.000Z",
         "topic": "technology",
         "author": "John Doe"
       },
       {
         "article_id": 2,
         "title": "The Latest in Sports",
         "body": "Updates on the latest sports events.",
         "votes": 50,
         "created_at": "2023-08-21T00:00:00.000Z",
         "topic": "sports",
         "author": "Jane Smith"
       }
     ]
     ```

5. **GET /api/articles/:article_id/comments**
   - Retrieves comments associated with a specific article.
   - **Response Example:**
     ```json
     [
       {
         "comment_id": 1,
         "body": "Great article!",
         "votes": 10,
         "created_at": "2023-08-20T12:00:00.000Z",
         "author": "Alice"
       },
       {
         "comment_id": 2,
         "body": "I completely agree.",
         "votes": 5,
         "created_at": "2023-08-21T14:00:00.000Z",
         "author": "Bob"
       }
     ]
     ```

6. **POST /api/articles/:article_id/comments**
   - Enables the addition of a comment to a specific article.
   - **Request Body Example:**
     ```json
     {
       "body": "This is a new comment.",
       "author": "Charlie"
     }
     ```
   - **Response Example:**
     ```json
     {
       "comment_id": 3,
       "body": "This is a new comment.",
       "votes": 0,
       "created_at": "2023-08-22T16:00:00.000Z",
       "author": "Charlie"
     }
     ```

7. **PATCH /api/articles/:article_id**
   - Allows updating details of a specific article.
   - **Request Body Example:**
     ```json
     {
       "title": "Updated Title",
       "body": "Updated body content."
     }
     ```
   - **Response Example:**
     ```json
     {
       "article_id": 1,
       "title": "Updated Title",
       "body": "Updated body content.",
       "votes": 100,
       "created_at": "2023-08-20T00:00:00.000Z",
       "topic": "technology",
       "author": "John Doe"
     }
     ```

8. **DELETE /api/comments/:comment_id**
   - Facilitates the deletion of a comment.
   - **Response Example:**
     ```json
     {
       "message": "Comment deleted successfully."
     }
     ```

## Additional Information

- **Database Schema:** Use PostgreSQL to manage data storage. Design tables for articles, comments, topics, and users with appropriate relationships.
- **Validation:** Ensure proper validation and sanitization of request data to maintain data integrity.
- **Error Handling:** Implement robust error handling to manage various scenarios such as invalid inputs or server errors.
- **Testing
