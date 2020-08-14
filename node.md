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
  };



//Tells server to listen at port(3000) to see a demo of our web app while developing. 
app.listen(3000, '127.0.0.1');
console.log('Node server running on port 3000');
```

4. In the command prompt, type in 
```node app.js``` and hit enter. You'll see something similar to this. 
```terminal
node server.js
//Node server started at port 3000
```

5. Open your browser and visit 
   http://localhost:3000. You should see a ```Hello World!``` message. 









//based on the challenge 
//framework
//server is handling data => performing actions with the data (CRUD)
//in order to spin up, there are steps to follow 
//creating full stack 
//app code running fast/quickly
//frontend-what users see
backend-data is stored 
//error handling: more example (in summary)
//guided practice 2.not clear => give clear examples 
//single thread = one person doing one work 
//one request at a time
//if it gets blocked it can work on other things

//NOde is a runtime env for executing js code
//Node is not a framework!
//Node apps are highly scalalable: non-blocking asynchronous and what is async? (analogy: one waiter serves and can serve another table while chef is cooking) by default
//Node is ideal for i/o intensive apps, Do not use Node for CPU-intensive apps
//i/o handles asynchrnously and the server thread can process other request in the meantime
//CPU-intensive other tasks like computing or non-io is not ideal for Node

//installing node
1. open terminal 
2. node --version (running node version)
3. open the browser and head over the nodejs.org
4. LTS Vs experimental -get LTS
5. continue and install

//building a node app
1. open the terminal
2. mkdir first-app //create a directory
3. cd into the first-app
4. code . (vs text editor, atom . for atom)
5. add a new file called app.js
6. in app.js you can write js code
7. ``` javascript
   function SayHello(name) {
       console.log('Hello ' + name);
   }
   sayHello('TLM');

8. To run the code: node app.js
//Modules
app.js is a main module
//how to create a load the module
1. add a new file - logger.js
   ```javascript
   var url = 'http://mylogger.io/log';
   //private module

   function log(message) {
       //send and HTTP request
       console.log(message);
   }
   
2. in order to export this private module to the main module (app.js) you will do 
```javascript
module.exports.log = log;
//loading module
require('./logger') or require('./logger.js')
```
Use const = > not to change the variable accidentally 

//exporting a single function
```javascript
module.exports = log;
```
//module wrapper function
```javascript 
exports.log = log; //module.exports
```
//node doc api modules
//Path module
in app.js
```javascript
const path = require('path');

var pathObj = path.parse(__filename);
console.log(pathObj)
```
//os module
```javascript
const os = require('os');

var totalMemory = os.totalmem();
var freeMemory = os.freemem();
//template string
console.log(`Total Memory: ${totalMemory}`);
console.log(`Free Memory: ${freeMemory}`);
```
//file system module
```javascript
const fs = require('fs');

const files = fs.readdirSync('./'); //returns all the files in the folder
fs.readdir('./', function(err, files) {
    if (err) console.log('Error', err);
    else console.log('Result', files);
});
```
//event: a signal that something had happened. HTTP uses for building webserver req - res
//how to work with event module
Events module
Class:EventEmitter

```javascript
//class starts with upper case (PascalCase)
const EventEmitter = require('events'); 
const emitter = new EventEmitter();

//register a listener
emitter.on('messageLogged', (arg) => {
    console.log('Listener called')

});
//Raise an event
emitter.emit('messageLogged', { id:1, url: 'http://'});

//emit making a noise or produce sometning - signalling event has happened


//the order matters. 

```
//class human (property), blue print
//object john (instance of the class)
//when the func is insdie the class, it is called method

class Logger extends EventEmitter
//Logger is inheriting everything from EventEmitter class

//http module = building networking app 
```javascript
const http = require('http');
const server = http.createServer((req, res)=> {
    if (req.url === '/'){
        res.write('Hello World');
        res.end();
    }
    if (req.url === '/api/courses'){
        res.wrtie(JSON.stringify([1,2,3]))
        res.end();
    }
}); //creates a web server


server.listen(3000);

console.log('Listening on port 3000...');

```

