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

## Explaining Server.js

```js

// load .env vars
require("dotenv").config;

// import dependencies
const express = require("express"); //framework
const morgan = require("morgan"); // logger
const methodOverride = require("method-override"); // override form posts
const session = require("express-session"); // middleware for managing session cookies
const connectMongo = require("connect-mongo"); // middleware for storing sessions in mongo

// Import Routers
const sampleRouter = require("./controllers/sample");

// get PORT, DATABASE_URL and SECRET variables from .env
const { PORT = 3000, DATABASE_URL, SECRET = "default" } = process.env;

// Create Express App Object
const app = express();

// Register Middleware
app.use(morgan("dev")); // logger
app.use(express.static("public")); // static folder for serving static assets
app.use(methodOverride("_method")); // override method with _method url query
app.use(express.urlencoded({ extended: true })); // parse urlencoded bodies
app.use(express.json()); // parse JSON bodies
app.use(
  session({
    secret: SECRET,
    resave: true,
    saveUninitialized: true,
    store: connectMongo.create({ mongoUrl: DATABASE_URL }),
  })
); // enable session cookies (store data in req.session between requests)

// Register Routes
app.use("/samples", sampleRouter);

// main route for "/" (all other routes should be handled by routers)
app.get("/", (req, res) => {
  res.send("Server is Working");
});

// turn on server
app.listen(PORT, () => {
  console.log(`Server listening on PORT ${PORT}`);
});


```

The provided code is a basic setup for a Node.js application using Express.js. It starts by loading environment variables and importing necessary dependencies such as Express (web framework), Morgan (logging middleware), Method-Override (to use HTTP verbs like PUT/DELETE in forms), and session management tools (express-session and connectMongo for storing sessions in MongoDB).

A custom router sampleRouter is imported for handling routes under "/samples". The application uses middleware for logging, serving static files, overriding methods, parsing request bodies, and managing session cookies. Session cookies are stored in MongoDB, configured with the DATABASE_URL from the environment variables. The secret key for sessions is also sourced from environment variables.

The application defines a main route ("/") that responds with "Server is Working" when accessed. Finally, the application listens on the specified PORT, displaying a console message when it starts.

Expected Output:
```
Server listening on PORT [port_number]
```
Here, [port_number] will be replaced with the actual port number specified in the .env file.