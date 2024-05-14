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
  - dls_auth_api
  - dls_dbChanges
  - dls_dbUserChanges
  - dls_cdnChanges
  - dls_frontend
  - dls_graphql
  - dls_write_api
  - dls_emailer
  - .env
  - docker-compose.yml


## Environment Variables

Create a .env in the root folder.

#JWT
JWT_SECRET='MmIxM2Q1NjNmNjA1YjNiYjZiNWY0M2VjOTVhMmFhZWVmMWQ3ODAwNDlkOTFkNjJlMGQ3YzA0ZDcwZDQ2ZGU0NA=='

#RabbitMQ
RABBITUSER='user'
RABBITPW='password'
RABBITURL='rabbitmq'

#MSSQL Write Database Frontend
WRITE_DB_SERVER='localhost,1433'
WRITE_DB_SERVER_PORT='1433'
WRITE_DB_INTERNAL_DOCKER_SERVER='write-db,1433'
WRITE_DB_INTERNAL_DOCKER_SERVER_NO_PORT='write-db'
DB_INTERNAL_DOCKER_SERVER_NAME='mssql'
DB_USER='SA'
DB_PASSWORD='YourStrongPassword123'
DB_FRONTEND='mssqlWrite'

#MSSQL Auth Backend
AUTH_DB_SERVER='localhost,1434'
AUTH_DB_INTERNAL_DOCKER_SERVER='auth-db,1433'
DB_BACKEND='usersDb'

#MongoDB
MONGOUSER='admin'
MONGOPW='Passw0rd!'
MONGOURL='@mongo:27017/admin'
MONGODB='read-db'

#Port specification
FRONTEND_PORT=8080
FRONTEND_BACKEND_PORT=4000
FRONTEND_WRITE_REST_PORT=3000

#URL's
GRAPHQLURL=http://localhost:4000/graphql
WRITEAPIURL=http://localhost:3000/v1
FRONTENDURL=http://localhost:8080
AUTHURL=http://localhost:5012/v1
CDNURL=http://localhost:9000/images/


## How To Run

Make sure the environment variables are set.<br>
Setup all the Repositories for this project and update them to the the development branch.<br>
Be in the root of the project with your terminal
Lastly, use the following command:

```bash
docker-compose up --build
```

## Setup Kubernetes

**DONT RUN UNLESS RESOLVED YAML IS MISSING**

```bash
docker-compose config > docker-compose-resolved.yaml
```

```bash
kompose convert -f docker-compose-resolved.yaml -o ./kubernetes 
```


## Run Kubernetes
Make sure the the docker images are built.<br>

then run 
```bash
kubectl apply -f ./kubernetes
```

check pods with

```bash
kubectl get pods
```

check services with
```bash
kubectl get services
```

to check the frontend, it has to be port forwarded
```bash
kubectl port-forward service/dls-frontend 8080:8080
```

to remove them again you can run

```bash
kubectl delete pods,services,deployments,replicasets --all
```

### How to port forward all services

```bash
Start-Job { kubectl port-forward svc/auth-backend 5012:5012 }
Start-Job { kubectl port-forward svc/auth-db 1434:1434 }
Start-Job { kubectl port-forward svc/cdn-changes 5020:5020 }
Start-Job { kubectl port-forward svc/db-changes 5000:5000 }
Start-Job { kubectl port-forward svc/db-user-changes 5001:5001 }
Start-Job { kubectl port-forward svc/dls-frontend 8080:8080 }
Start-Job { kubectl port-forward svc/emailer 5050:5050 }
Start-Job { kubectl port-forward svc/graphql-api 4000:4000 }
Start-Job { kubectl port-forward svc/mongo 27017:27017 }
Start-Job { kubectl port-forward svc/nginx 9000:9000 }
Start-Job { kubectl port-forward svc/rabbitmq 15672:15672 }
Start-Job { kubectl port-forward svc/rabbitmq 5672:5672 }
Start-Job { kubectl port-forward svc/write-api 3000:3000 }
Start-Job { kubectl port-forward svc/write-db 1433:1433 }
```