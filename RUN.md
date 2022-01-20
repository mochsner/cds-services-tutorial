dock-compose up --build

Running the project
Depending on your tool choice, use one of the following methods to start the project:

Node.js
Once you're inside the project directory, type the command npm install to install all dependencies for the project.
If the above steps have all been done successfully, you can run the project by typing the command npm run start-server.
Docker
Once you're inside the project directory, type the command docker-compose up --build to build the image and start the container.
This will start the express application, which will be hosted locally for you, and can be accessible at:

http://localhost:3000
Docker Cleanup
The container can be stopped by breaking with Ctrl-C.
To remove the container and image from your machine, type the command docker-compose down --rmi all.
How it Works
Let's look at how this application starts up. Begin by looking inside the project directory at the index.js file, which is where all the host code for our Express application lives. You can open up this file with any text editor of your choice and walk through the code for this tutorial.

const express = require('express');
const bodyParser = require('body-parser');
const app = express();
The first 2 lines of code are creating variables that reference two very important dependencies. We pulled these dependencies in via the command npm install from above.

express - As we mentioned above, Express is a framework for Node.js which allows us to use several HTTP methods to handle routing, as well as middleware.
body-parser - This dependency is a middleware necessary to parse the body of an incoming request; specifically, from POST requests. This allows the application to get data the EHR may send in a POST request to our CDS Services.
On that last line above, we construct an Express instance in a variable called app that will expose the Express API that we can use throughout our application.

At this point, we can define a middleware that will parse incoming request bodies to our services as JSON, for those potential POST HTTP requests.

...
app.use(bodyParser.json());
...
And finally, we need to allow the app to be hosted on some port, so let's define this app to listen in at port 3000 for the purposes of this tutorial. We can define this at the bottom of the application.

...
app.listen(3000);
Next step: Cross Origin Resource Sharing (CORS)
