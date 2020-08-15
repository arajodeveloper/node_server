# Introduction to Node.js and setting up the node server

## Video Lecture
<p>Coming Soon!

---

## Overview
* Node.js is for input/output (I/O) intensive, and fast applications. It is not good for CPU intensive tasks, for example, Video/Audio conversion and compression algorithms, long math computations
* Node.js uses a single thread running an event loop, and has async I/O. Analogy: A waiter (single threaded event loop) takes orders and serves tables but he can only do one thing at a time, so he tells the chef (someone else) to handle the cooking (async IO). When an event happens (food is ready), the waiter can get it and bring it to the customer.
* Node.js uses event driven programming, where the flow of execution is determined by events like query results coming back from the database, or a file being read.
---

## Learning Objectives
* Understanding the HTTP module
* Setting up the Node server with the HTTP module
* Understanding the basics of event-driven programming  
  
---

## Vocabulary
* Node (Node.js)
* http module
* response
* request
* event handlers
* callbacks
* listen 
* status code 
---

## Useful Resources
What is event-driven programming: [Event-driven programming](https://medium.com/@vsvaibhav2016/introduction-to-event-driven-programming-28161b79c223)

How Node.js works: [Node.js Server](https://media.geeksforgeeks.org/wp-content/uploads/20200224050909/nodejs2.png)

---

## What is Node.js? 
<p>Node.js is a free and open source environment for running JavaScript outside of a browser. We often use it to build backend services called api's (application programming interfaces) that power our client applcations like a web app running inside of a web browser or mobile app running on a mobile device. These apps (for example, facebook) are what the user sees and interacts with. They are just the surface. They need to talk to some backend services sitting on the server or in the cloud to store data, send emails, or push notifications and so on. But there are other backend frameworks such as rails, Django and so on. Why use Node.js?

---

## Why Use Node.js?
<p>Node is easy to get started and helps to build super fast services. It's used in production by large companies such as PayPal, Uber, Netflix, and Walmart. According to Jeff Harrell, Director of Engineering at PayPal, their Node.js-based app needed 33% fewer lines of code, handled double the number of requests per second, and shortened response time by 35% compared to the Java version. Node uses JS. If you are frontend developer using JS, you can also use Node.js to build a backend easily. Your source code is cleaner and consistent. Node also has a lot of free libraries available to help finish your projects faster. </p>
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

    //Pass a callback to the createServer() method. This callback tells the server to respond with "Hello World!" when it gets a request
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
   http://localhost:3000. You should see a  ```Hello World!``` message. 


## Challenge

* Set up a node server that shows your favorite quote in your browser!






