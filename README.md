# SunBaseData
 SunBase Backend Assignment - Shivanshu Mishra

 The Sunbase Customer Management Application is a web-based application that allows users to manage customer information. The application is built using Node.js and
 Express on the backend uses EJS as the template engine for rendering HTML pages on the front end.

Dependencies
The Sunbase Customer Management Application uses the following main dependencies:

express: Node.js web framework for building the backend.
ejs: Template engine for rendering HTML pages.
body-parser: Middleware for parsing request bodies.
cors: Middleware for enabling Cross-Origin Resource Sharing.
node-fetch: Library for making HTTP requests from the backend.

explanation of the codebase and their functionalities:

1. **app.js**:

   ```javascript
   const express = require("express");
   const bodyParser = require("body-parser");
   const cors = require("cors");
   const fetch = require("node-fetch");
   const session = require("express-session");

   const app = express();

   app.use(
     session({
       secret: "your_secret_key_here", // Replace with a secure secret key
       resave: false,
       saveUninitialized: true,
     })
   );

   app.use(bodyParser.urlencoded({ extended: true }));
   app.use(bodyParser.json()); // Add this line to parse JSON data

   app.use(cors());

   app.set("view engine", "ejs");
   ```

   Explanation:
   - This file is the main entry point of the application, where we initialize the Express server and set up the required middleware.
   - We import necessary modules such as `express`, `body-parser`, `cors`, `node-fetch`, and `express-session`.
   - We set up the `express-session` middleware to enable session management for user authentication.
   - We use `bodyParser` middleware to parse incoming request bodies.
   - We set the view engine to `ejs` for rendering EJS templates.

2. **login.ejs**:

   ```html
   <!DOCTYPE html>
   <html lang="en">
   <head>
       <!-- ... -->
   </head>
   <body>
       <!-- Login form -->
       <form action="/login" method="post">
           <!-- ... -->
       </form>
   </body>
   </html>
   ```

   Explanation:
   - This file is an EJS template representing the login page of the application.
   - It contains a simple login form with fields for the user to enter their login credentials (login_id and password).
   - The form is submitted to the `/login` route using the POST method.

3. **customers.ejs**:

   ```html
   <!DOCTYPE html>
   <html lang="en">
   <head>
       <!-- ... -->
   </head>
   <body>
       <!-- Customer list table -->
       <table class="table">
           <thead>
               <!-- ... -->
           </thead>
           <tbody>
               <% userData.forEach(user=> { %>
                   <!-- ... -->
               <% }); %>
           </tbody>
       </table>

       <!-- JavaScript code for deleting and editing customers -->
       <script>
           // JavaScript code for deleting a customer
           function deleteUser(uuid) {
               // Fetch API call to delete a customer
               fetch('/api/delete-user', {
                   method: 'POST',
                   headers: {
                       'Content-Type': 'application/x-www-form-urlencoded'
                   },
                   body: `uuid=${uuid}`
               })
               .then(response => {
                   // Handle the response (success or error)
               })
               .catch(error => {
                   // Handle the error
               });
           }

           // JavaScript code for editing a customer
           function editUser(user) {
               // Fetch API call to edit a customer
               fetch('/api/edit-user', {
                   method: 'POST',
                   headers: {
                       'Content-Type': 'application/json'
                   },
                   body: user
               })
               .then(response => {
                   // Handle the response (success or error)
               })
               .catch(error => {
                   // Handle the error
               });
           }
       </script>
   </body>
   </html>
   ```

   Explanation:
   - This file is an EJS template representing the customer list page of the application.
   - It renders a table displaying customer information fetched from the backend (provided as `userData`).
   - For each customer in the `userData` array, a table row is generated to display their details.
   - Each row contains "Delete" and "Edit" buttons that call JavaScript functions (`deleteUser` and `editUser`) to interact with the backend API.

4. **add_customer.ejs**:

   ```html
   <!DOCTYPE html>
   <html lang="en">
   <head>
       <!-- ... -->
   </head>
   <body>
       <!-- Add customer form -->
       <form action="/add-customer" method="post">
           <!-- ... -->
       </form>
   </body>
   </html>
   ```

   Explanation:
   - This file is an EJS template representing the "Add Customer" page of the application.
   - It contains a form with fields for entering customer information, such as first name, last name, address, email, etc.
   - The form is submitted to the `/add-customer` route using the POST method.

These files work together to create a simple customer management application. The `login.ejs` file provides a login form for users to enter their credentials. After successful login, users are redirected to the `customers.ejs` file, which displays a list of customers and allows users to add, delete, and edit customer information. The `add_customer.ejs` file provides a form for adding new customers. The JavaScript code in `customers.ejs` enables interaction with the backend API for deleting and editing customers.

##Screenshots

![login](https://github.com/shivanshum/SunBase-Express-EJS/assets/53150676/a75916a6-66d7-40ec-921e-53fa202d18a5)

![add_customer](https://github.com/shivanshum/SunBase-Express-EJS/assets/53150676/c6ffb5f5-cc6c-4880-9880-1b1b41516bf1)

![customer_list](https://github.com/shivanshum/SunBase-Express-EJS/assets/53150676/1d009f83-6cb3-44c5-aaf1-ed7bf10b2d69)

