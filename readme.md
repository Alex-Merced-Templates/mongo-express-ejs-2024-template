# Mongo/Express/EJS Template 2024

## Setup

1. Fork & Clone this repo (Or Generate From Template then clone)
2. Rename `sample.env` to `.env`
3. Write the values in the `.env` that you need, read the comments
4. Install dependencies `npm install`

## Explanation of NPM Scripts

1. **start**: `node server.js`
   - Runs the server using Node.js. This is typically used in production environments.

2. **dev**: `node --watch server.js`
   - Runs the server with the Node.js `--watch` flag, which automatically restarts the server when file changes are detected. Similar to Nodemon, but it's a newer feature in Node.js itself.

3. **dev-nodemon**: `nodemon server.js`
   - Runs the server using Nodemon, a utility that monitors for any changes in your source and automatically restarts your server.

4. **seed**: `node models/seed.js`
   - Executes the `seed.js` script to populate the MongoDB database with initial data, often used for setting up a development environment with test data.

These scripts provide convenient ways to start the server and manage the development workflow, especially the live-reloading features for development.




### Explanation of Initial NPM Dependencies

1. **bcrypt (v5.1.1)**: A library for hashing and comparing passwords securely. It's essential for storing user passwords in a safe manner.

2. **connect-mongo (v5.1.0)**: Middleware for Express.js to store session data in MongoDB. Useful for managing user sessions persistently.

3. **dotenv (v16.3.1)**: Loads environment variables from a `.env` file into `process.env`, providing a secure way to manage configuration settings.

4. **ejs (v3.1.9)**: A templating engine for creating HTML templates with embedded JavaScript. It's used for rendering views on the server side.

5. **express (v4.18.2)**: A minimal and flexible Node.js web application framework, providing a robust set of features for web and mobile applications.

6. **express-session (v1.17.3)**: A session middleware for Express.js, used to handle user sessions across multiple page requests.

7. **method-override (v3.0.0)**: Allows the use of HTTP verbs such as PUT or DELETE in places where the client doesn't support it.

8. **mongoose (v8.0.3)**: An ODM (Object Data Modeling) library for MongoDB and Node.js. It manages relationships between data and provides schema validation.

9. **morgan (v1.10.0)**: An HTTP request logger middleware for Node.js, useful for logging request details for debugging and monitoring.
