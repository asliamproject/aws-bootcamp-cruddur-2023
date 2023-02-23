# Week 1
## Summary

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

### Gitpod free-tier
>User Steeings>Billing>Free Tier Monthly 500 credit/50 hours 
### dockerhub, render, JFrog
[Dockerhub](https://hub.docker.com/)
[render](https://render.com/)
[JFrog](https://jfrog.com/)
## Ref
