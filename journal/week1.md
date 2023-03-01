# Week 1
## Summary
1. I have setup a new Github codespace for the project.
2. I have created the .gitpod and docker-compose yml files. Clone frontend and backend repo. Write Dockerfiles. 
3. I have gained knowledge and practiced common docker command.
4. I have built the container. Run the containers. Checked the env variable. Checked container logs.
5. I have run the backend and frontend containers together to lauch the Cruddur app.
6. I have used Gipod to modify /backend-flask/services/messages.py file.
7. I have created notifications endpoint.


### create Github codespace.
![image](https://user-images.githubusercontent.com/116926319/221101177-63928bbd-9ffe-476b-9682-1f46ef9e1961.png)

to run codein Github codespace:
```
FRONTEND_URL: "https://${CODESPACE_NAME}-3000.${GITHUB_CODESPACES_PORT_FORWARDING_DOMAIN}"
BACKEND_URL: "https://${CODESPACE_NAME}-4567.${GITHUB_CODESPACES_PORT_FORWARDING_DOMAIN}"
REACT_APP_BACKEND_URL: "https://${CODESPACE_NAME}-4567.${GITHUB_CODESPACES_PORT_FORWARDING_DOMAIN}"
```

### Steps1. Backend Install
1. create backend-flask folder
2. Copy & create Dockerfile
3. Terminal:

```
pip3 install -r requirements.txt
cd backend-flask
export FRONTEND_URL="*"
export BACKEND_URL="*"
python3 -m flask run --host=0.0.0.0 --port=4567

```

make sure to unlock the port on the port tab\
open the link for 4567 in your browser\
append to the url to /api/activities/home\
you should get back json

```
FROM python:3.10-slim-buster

WORKDIR /backend-flask

COPY requirements.txt requirements.txt
RUN pip3 install -r requirements.txt

COPY . .

ENV FLASK_ENV=development

EXPOSE ${PORT}
CMD [ "python3", "-m" , "flask", "run", "--host=0.0.0.0", "--port=4567"]
```

CHECK VARIABLE EXAMPLE
```
$env | grep VARIABLE
$env | grep BACKEND
$env | grep _URL
```

REMOVE VARIABLE EXAMPLE
```
unset BACKEND_URL
```

BUILD CONTAINER
```
docker build -t  backend-flask ./backend-flask
```

LOCATE IMAGES
```
$ docker images
$ docker build --help
```

RUN
```
docker run --rm -p 4567:4567 -it -e FRONTEND_URL='*' -e BACKEND_URL='*' backend-flask
```

###ONLY USE SINGLE QUOTE IN THE ABOVE COMMAND

![image](https://user-images.githubusercontent.com/116926319/220831424-c0d97b44-e646-4a36-919c-9d11ea42e224.png)

CHECK DOCKER LOG AND ENV
```
docker exec -it
```

OR right click Docker file > Select Attach Shell from the drop down manu
![image](https://user-images.githubusercontent.com/116926319/220829240-22096b5e-b090-4517-b31c-8979cdd9d1ab.png)

SET ENV
(https://docs.docker.com/compose/environment-variables/set-environment-variables/)

### Steps2. Frontend Install
```
cd frontend-react-js
npm i
```
Compose
![image](https://user-images.githubusercontent.com/116926319/220870382-030bfc3d-c841-46cd-be9b-809da8732459.png)
![image](https://user-images.githubusercontent.com/116926319/220872358-bc34d13e-1e16-427e-aaad-be79b2bb440e.png)
![image](https://user-images.githubusercontent.com/116926319/220872448-845caf4f-cf42-4f93-aa01-104e38b0cb57.png)

### Steps3. Create DynamoDB Local and Postgres
![Screenshot_20230225_055138](https://user-images.githubusercontent.com/116926319/221343628-5953c1a1-0c51-40f8-a55d-e1b52232dfcb.png)
![Screenshot_20230225_055551](https://user-images.githubusercontent.com/116926319/221343629-d6c84b4d-6782-4b3a-847e-b60c5c383725.png)

### create notification backend endpoint
![Screenshot_20230225_060141](https://user-images.githubusercontent.com/116926319/221343683-8152bf2a-467f-4857-b794-1b06b93cb4b9.png)

### Gitpod free-tier
>User Steeings>Billing>Free Tier Monthly 500 credit/50 hours 
>
### dockerhub, render, JFrog
[Dockerhub](https://hub.docker.com/)
[render](https://render.com/)
[JFrog](https://jfrog.com/)

## Ref
1.[DynamoDBLocal](https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/DynamoDBLocal.html)
2.(https://github.com/100DaysOfCloud/challenge-dynamodb-local)
