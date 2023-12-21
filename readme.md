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




## Explanation of Initial NPM Dependencies

1. **bcrypt (^5.1.1)**: A library for hashing and comparing passwords securely. It's used to encrypt passwords before storing them in a database.

2. **connect-mongo (^5.1.0)**: A MongoDB session store for Express.js, used with express-sessions for storing session data in MongoDB.

3. **dotenv (^16.3.1)**: Loads environment variables from a `.env` file into `process.env`, providing a secure way to store configuration details outside of code.

4. **ejs (^3.1.9)**: Embedded JavaScript templating engine. It's used to generate HTML markup with plain JavaScript.

5. **express (^4.18.2)**: A minimal and flexible Node.js web application framework, providing a robust set of features for web and mobile applications.

6. **express-sessions (^1.0.6)**: An Express.js middleware for managing sessions, used for maintaining user data between HTTP requests.

7. **method-override (^3.0.0)**: Middleware to use HTTP verbs such as PUT or DELETE in places where the client doesn't support it.

8. **morgan (^1.10.0)**: HTTP request logger middleware for Node.js, used for logging request details.
