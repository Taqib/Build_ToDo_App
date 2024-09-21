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

todo-service/package.json
This file defines the Node.js project configuration for the ToDo Service

todo-service/index.js
This is the main entry point of the ToDo Service

express: Sets up the Express server.
dotenv: Loads environment variables from the .env file.
todoController: Handles task-related operations.

todo-service/todoController.js
This file contains the controller logic for the ToDo Service

getTasks: Retrieves all tasks from Redis.
getTaskById: Retrieves a task by ID from Redis.
addTask: Adds a new task to Redis.
deleteTask: Deletes a task by ID from Redis.

Docker Compose
docker-compose.yml
This file defines the Docker services

Running the Application
Navigate to the root directory of the project.

Build and start the Docker containers.

docker-compose up --build
The API Gateway should now be running on http://localhost:5000 and the ToDo Service on http://localhost:8000.

You can interact with the API Gateway to manage tasks.

GET http://localhost:5000/: Fetches all tasks.
GET http://localhost:5000/<task_id>: Fetches a specific task by ID.
POST http://localhost:5000/: Adds a new task.
DELETE http://localhost:5000/<task_id>: Deletes a task by ID.
For example, to add two new task:

curl -X POST http://localhost:5000/ -H "Content-Type: application/json" -d '{"task": "Sample Task 1"}'

curl -X POST http://localhost:5000/ -H "Content-Type: application/json" -d '{"task": "Sample Task 2"}'
To retrieve all tasks:

curl http://localhost:5000/

