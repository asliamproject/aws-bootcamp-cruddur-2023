# Week 1
## Summary

### Steps
1. create backend-flask folder
2. Copy Dockerfile
'''
FROM python:3.10-slim-buster

WORKDIR /backend-flask

COPY requirements.txt requirements.txt
RUN pip3 install -r requirements.txt

COPY . .

ENV FLASK_ENV=development

EXPOSE ${PORT}
CMD [ "python3", "-m" , "flask", "run", "--host=0.0.0.0", "--port=4567"]
'''

### Gitpod free-tier
>User Steeings>Billing>Free Tier Monthly 500 credit/50 hours 
### dockerhub, render, JFrog
[Dockerhub](https://hub.docker.com/)
[render](https://render.com/)
[JFrog](https://jfrog.com/)
## Ref
