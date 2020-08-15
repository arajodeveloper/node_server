# Setting Up A Node Server

## Video Lecture
---


## Overview
* Node.js is for asynchronous, non-blocking, I/O intensive, and fast applications (Not for CPU intensive)
* Node.js uses a single thread with event looping (Analogy: a waiter can serve different tables while chef cooks food. Waiter does not have to wait to serve another table until food is served)
* Node.js is an event driven programming which flow of execution is determined by the events like user clicks or other programming threads or query results from database. Events are handled by event handlers or event callbacks 
---

## Learning Objectives
* Understanding the HTTP module and importing it in app.js file
* Setting up the Node server using HTTP module
* Understanding basic event-driven programming pardigm 
  
---

## Vocabulary
* Node(Node.js)
* http module
* response
* request
* event handlers
* callbacks
* listen 
* node app.js
* port
* 200 status code 
---

## Useful Resources
---

## What is Node.js? 
<p>Node.js is a JavaScript free and open source cross-platform runtime environment for executing JavaScript code outside of a browser. We often use it to build backend services also called api's (application programming interface) that power our client applcations like a web app running inside of a web browser or mobile app running on a mobile device. These apps are simply what the user sees and interacts with. They are just the surface. They need to talk to some services sitting on the server or in the cloud to store data, send emails, or push notifications and so on. Node is ideal for building highly scalable data-intensive and real-time backend services that power our client applciations. But there are other backend services framework such as rails, Django and so on. Why use Node.js?

---

## Why Use Node.js?
<p>Node is easy to get started and can be used building super fast and highly scalable services. It's used in production by large companies such as PayPal, Uber, Netflix, and Walmart. Node app was built twice as fast with fewer people. 33% fewer lines of code. and 40% fewer files. 2 times fast request per second while 35% faster response time. Node uses JS. If you are frontend developer using JS, you can also use Node.js to build backend quick. YOur source code is cleaner and consistent. Large ecosystem of open-source library, so a lot of things can be built using libraries. </p>
---

## How to set up a node server?
---
Writing web apps with Node involves writing event handlers that get called when certain Node events occur. Let's see an example.

1. Create a new folder, cd into the folder with your terminal or command prompt.
   
```terminal
mkdir node-intro
cd node-intro
```
2. Do an  ```npm init```, hit enter till you successfully create a ```package.json``` file in the root of the folder.
3. Create an ```app.js``` file in the root folder, copy and paste the code below.

```Javascript
//app.js

//http module
const http = require ('http');

//Pass a callback to the createServer() method, Node adds the request event handler for us.
let app = http.createServer((request, response)=> {
  //Attach some headers to the server's response(Status code and content type)
  response.writeHead(200, {'Content-Type':'text/plain'});
  //Send back a response and end the connection to the server
  response.end('Hello World!\n');
});



//Tells server to listen at port(3000) to see a demo of our web app while developing. 
app.listen(3000, '127.0.0.1');
console.log('Node server running on port 3000');
```

4. In the command prompt, type in 
```node app.js``` and hit enter. You'll see something similar to this. 
```terminal
node app.js
//Node server running on port 3000
```

5. Open your browser and visit 
   http://localhost:3000. You should see a ```Hello World!``` message. 









