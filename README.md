This To-Do App project demonstrates a microservices architecture using Node.js, Express, and Redis. It comprises two main services: an API Gateway and a ToDo Service. The API Gateway handles client requests and forwards them to the ToDo Service, which manages task data stored in a Redis database. Docker Compose is used to manage the deployment and orchestration of these services.

Project Structure

todo-app/
│
├── api-gateway/
│   ├── node_modules/
│   ├── .env
│   ├── package.json
│   ├── index.js
│   └── routes.js
│
├── todo-service/
│   ├── node_modules/
│   ├── .env
│   ├── package.json
│   ├── index.js
│   └── todoController.js
│
└── docker-compose.yml

Directory Breakdown
api-gateway/: Contains the API Gateway code, handling client requests and routing them to the ToDo Service.
todo-service/: Contains the ToDo Service code, which interacts with Redis to manage tasks.
docker-compose.yml: Defines the Docker services for the API Gateway, ToDo Service, and Redis.

API Gateway
api-gateway/.env
This file contains environment variables for the API Gateway:

PORT: The port on which the API Gateway runs.
TODO_SERVICE_URL: The URL of the ToDo Service.

api-gateway/package.json
This file defines the Node.js project configuration for the API Gateway

api-gateway/index.js
This is the main entry point of the API Gateway

express: Sets up the Express server.
dotenv: Loads environment variables from the .env file.
routes: Imports routes from routes.js.

api-gateway/routes.js
This file defines the routes for the API Gateway, using Axios to communicate with the ToDo Service

GET /tasks: Fetches all tasks from the ToDo Service.
GET /tasks/:id: Fetches a specific task by ID from the ToDo Service.
POST /tasks: Adds a new task via the ToDo Service.
DELETE /tasks/:id: Deletes a task by ID via the ToDo Service.

todo-service/.env
This file contains environment variables for the ToDo Service

PORT: The port on which the ToDo Service runs.
REDIS_URL: The URL of the Redis database.

