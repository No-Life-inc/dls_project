# DLS Project

## Contributors

- Morten Bendeke
- Betül Iskender
- Yelong Hartl-He
- Zack Ottesen

## General Use

This is created to build the full project in a docker environment <br>
The full struckture of the project should look like this:<br>
- dls_project
  - dls_backend
  - dls_dbChanges
  - dls_dbUserChanges
  - dls_frontend
  - dls_frontend_backend
  - dls_frontend_write_rest_api
  - .env
  - docker-compose.yml


## Environment Variables

Create a .env in the root folder.

#JWT
JWT_SECRET='2b13d563f605b3bb6b5f43ec95a2aaeef1d780049d91d62e0d7c04d70d46de44'

#RabbitMQ
- RABBITUSER='user'
- RABBITPW='password'
- RABBITURL='rabbitmq'

#MSSQL Frontend and Backend
- DB_SERVER='localhost,1433'
- DB_INTERNAL_DOCKER_SERVER='mssql,1433'
- DB_INTERNAL_DOCKER_SERVER_NAME='mssql'
- DB_USER='SA'
- DB_PASSWORD='YourStrongPassword123'
- DB_BACKEND='usersDb'
- DB_FRONTEND='mssqlWrite'

#MongoDB
- MONGOUSER='admin'
- MONGOPW='Passw0rd!'
- MONGOURL='@mongo:27017/admin'
- MONGODB='frontend_backend_db'

#Port specification
- FRONTEND_PORT=3001 #PORT
- FRONTEND_BACKEND_PORT=4000 #PORT
- FRONTEND_WRITE_REST_PORT=3000 #PORT

#GraqhQL and WriteAPI
- GRAPHQLURL=http://localhost:4000/graphql
- WRITEAPIURL=http://localhost:3000
- FRONTENDURL=http://localhost:3001

## How To Run

Make sure the environment variables are set.<br>
Setup all the Repositories for this project and update them to the the development branch.<br>
Be in the root of the project with your terminal
Lastly, use the following command:

```bash
docker-compose up --build
```

