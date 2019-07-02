# Homework: Full Stack Games Hub App

### Learning Objectives

- Understand the relationship between client, server and database
- Be able to navigate a codebase that you haven't written

## Brief

Your boss has asked to you look over the codebase of a full-stack JavaScript application. The front-end is written in JavaScript using Vue, the back-end uses an Express server and a MongoDB database. Your task is to make yourself familiar with the codebase.

The application includes a README.md with instructions on running the application.

![Overview of the tech stack and tooling with commands](images/tech_stack_with_commands.png)

*Overview of the tech stack and tooling with commands*

## MVP

### Task

Draw a diagram showing the dataflow through the application starting with a form submission, ending with the re-rendering of the page. This will involve a multi-direction data-flow with the client posting data to the server and the server sending data back to the client with the response. Detail the client, server and database in the diagram and include the names of the files involved in the process.

### Questions

1. What is responsible for defining the routes of the `games` resource?
The create_router.js file defines the routes along with the server.js provides the prefix in the app.use() method call.

2. What do you notice about the folder structure?  Whats the client responsible for? Whats the server responsible for?
The files are separated based on their responsibilities either to the client side or the server side.
The client handles any user input and sends the request to the correct route based on the input.
The server connects to the database and listens for any incoming requests and then sending the response after actioning the request.

3. What are the the responsibilities of server.js?
The server.js file connects to the mongo database and creates the games_hub database containing the games collection. It then makes the call to express to create the routes. It continually listens on port 3000 for incoming requests.

4. What are the responsibilities of the `gamesRouter`?
The gamesRouter defines the routes for each of the endpoints and invokes the appropriate function based on the method type on the request.

5. What process does the the client (front-end) use to communicate with the server?
The client uses the functions available in the GameService.js file to do this.

6. What optional second argument does the `fetch` method take? And what is it used for in this application? Hint: See [Using Fetch](https://developer.mozilla.org/en-US/docs/Web/API/Fetch_API/Using_Fetch) on the MDN docs
The second argument is an object which specifies settings that the fetch request should use.

7. Which of the games API routes does the front-end application consume (i.e. make requests to)?
The app makes requests to the below routes:
/api/games/  ( a get and a post )
/api/games/:id  ( a delete )

8. What are we using the [MongoDB Driver](http://mongodb.github.io/node-mongodb-native/) for?
We use it for creating a non-relational database to store entries in JSON-style documents. As we are using JavaScript to query the database it is ideal in storing JavaScript objects.

## Extension

Why do we need to use [`ObjectId`](https://mongodb.github.io/node-mongodb-native/api-bson-generated/objectid.html) from the MongoDB driver?
MongoDB assigns unique ObjectIds when we insert entries into the database. We can use the ObjectId constructor to find the entries again when querying the database to perform CRUD operations.

Add to your diagram the dataflow for removing a game.
