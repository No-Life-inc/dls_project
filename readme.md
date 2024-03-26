# REPO TEMPLATE

## Contributors

- Morten Bendeke
- Betül Iskender
- Yelong Hartl-He
- Zack Ottesen

## General Use

What are the main use cases for the project? <br>
How is the code located in the repository used? <br>
- PLACEHOLDER: VALUE.

## Environment Variables

Create a .env in the root folder.

#JWT

JWT_SECRET='2b13d563f605b3bb6b5f43ec95a2aaeef1d780049d91d62e0d7c04d70d46de44'

#RabbitMQ

RABBITUSER='user'
RABBITPW='password'
RABBITURL='rabbitmq'

#MSSQL Frontend and Backend

DB_SERVER='localhost,1433'
DB_INTERNAL_DOCKER_SERVER='mssql,1433'
DB_INTERNAL_DOCKER_SERVER_NAME='mssql'
DB_USER='SA'
DB_PASSWORD='YourStrongPassword123'
DB_BACKEND='usersDb'
DB_FRONTEND='mssqlWrite'

#MongoDB

MONGOUSER='admin'
MONGOPW='Passw0rd!'
MONGOURL='@mongo:27017/admin'
MONGODB='frontend_backend_db'

#Port specification

FRONTEND_PORT=3001 #PORT
FRONTEND_BACKEND_PORT=4000 #PORT
FRONTEND_WRITE_REST_PORT=3000 #PORT

#GraqhQL and WriteAPI

GRAPHQLURL=http://localhost:4000/graphql
WRITEAPIURL=http://localhost:3000
FRONTENDURL=http://localhost:3001





## How To Run

Make sure the environment variables are set.<br>
More Steps.<br>
Lastly, use the following command:

```bash
run PLACEHOLDER
```

## Dependencies

What dependencies are used and why.
