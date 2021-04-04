# Games Video API

> Backend API for Games Video application

# Usage

## Install Dependencies

```
npm install
```

## Run in prod mode

> npm start

Database Seeder
To seed the database with users, Video Games, users and reviews with data from the "\_data" folder, run

## Destroy all data

> node seeder -d

## Import all data

> node seeder -i

# Demo

> The API Link : [https://play-area.herokuapp.com/](https://play-area.herokuapp.com/)

# Documentation

> Extensive documentation with examples : [Here](https://documenter.getpostman.com/view/13825305/TzCQaRcs#51f35aa5-3a79-4d2a-8840-711930b932e3)

For documentation choose an envirenement for the api docs


```
-Version: 1.2.0

-License: MIT

-Author: Moulahi Mohammed
```

# Details

# Video Games/reviews Backend API Specifications

Create the backend for a Video Games directory website. The frontend/UI will be created by another team (future review). The template has been created and can be used as a reference for functionality. All of the functionality below needs to be fully implmented in this project.

## Video Games

- List all Video Games in the database
  - Pagination
  - Select specific fields in result
  - Limit number of results
  - Filter by fields
- Get single Product
- Create new Video Games
  - Authenticated users only
  - Must have the role "publisher" or "admin"
  - Only one Video Games per Moderator (admins can create more)
  - Field validation via Mongoose
- Upload a photo for Video Game
  - Owner only
  - Photo will be uploaded to local filesystem
- Update Video Games
  - Owner only
  - Validation on update
- Delete Video Games
  - Owner only
- Calculate the average rating of all Video Games
- Calculate the average rating from the reviews for a Video Games

## Reviews

- List all reviews for Video Games
- List all reviews in general
  - Pagination, filtering, etc
- Get single review
- Create new review
  - Authenticated users only
  - Must have the role "publisher" or "admin"
  - Only the owner or an admin can create a review for a Video Games
  - Publishers can create multiple reviews
- Update review
  - Owner only
- Delete review
  - Owner only

## Users

- List all users for a Video Games
- List all users in general
  - Pagination, filtering, etc
- Get a single users
- Create a users
  - Authenticated users only
  - Must have the role "user" or "admin" (no publishers)
- Update users
  - Owner only
- Delete users
  - Owner only

## Users & Authentication

- Authentication will be ton using JWT/cookies
  - JWT and cookie should expire in 30 days
- User registration
  - Register as a "user" or "publisher"
  - Once registered, a token will be sent along with a cookie (token = xxx)
  - Passwords must be hashed
- User login
  - User can login with email and password
  - Plain text password will compare with stored hashed password
  - Once logged in, a token will be sent along with a cookie (token = xxx)
- User logout
  - Cookie will be sent to set token = none
- Get user
  - Route to get the currently logged in user (via token)
- Password reset (lost password)
  - User can request to reset password
  - A hashed token will be emailed to the users registered email address
  - A put request can be made to the generated url to reset password
  - The token will expire after 10 minutes
- Update user info
  - Authenticated user only
  - Separate route to update password
- User CRUD
  - Admin only
- Users can only be made admin by updating the database field manually

## Middlewares

- Filtring Middleware : to filter query requests from clients.
- Authorization Middleware : to filter whose roles

  `['Admin' ,'Moderator','User']`

  that have access and claims to each route requests.

- CheckAuth Middleware : to check is Auth before get access to a specific route.

## Sending Mails

- After user successfully signed up a confirmation mail is send to his email adress.

- On a Rest Password request a mail is send to user email with a link to reset his password with a expiration delai ( 60 mins).

## Security

- Encrypt passwords and reset tokens
- Prevent cross site scripting - XSS
- Prevent NoSQL injections
- Add a rate limit for requests of 100 requests per 15 minutes
- Protect against http param polution
- Add headers for security (helmet)
- Use cors to make API public (for now)

## Documentation

- Use Postman to create documentation
- Use docgen to create HTML files from Postman
- Add html files as the / route for the api

## Deployment (Heroku / Github)

- Push to Github
- Create a dynos at Heroku - https://play-area.herokuapp.com/

## Code Related Suggestions

- NPM scripts for dev and production env
- Config file for important constants
- Use controller methods with documented descriptions/routes
- Error handling middleware
- Authentication middleware for protecting routes and setting user roles
- Validation using Mongoose and no external libraries
- Use async/await (create middleware to clean up controller methods)
- Create a database seeder to import and destroy data
