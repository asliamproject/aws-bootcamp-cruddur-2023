# Week 6 Fargate
## Test RDS Connecetion
```
$ export GITPOD_IP=$(curl ifconfig.me)
./bin/rds/update-sg-rule
./bin/db/test
./bin/flask/health-check
```
## Create Cluster

### Create Cloudwatch log group
: cruddur

### Elastic Container Service
Clusters: cruddur

### Login
```
aws ecr get-login-password --region $AWS_DEFAULT_REGION | docker login --username AWS --password-stdin "$AWS_ACCOUNT_ID.dkr.ecr.$AWS_DEFAULT_REGION.amazonaws.com"
```

### Create Repo
Elastic Container Registry
Repostitory Name: cruddur-python
```
export ECR_PYTHON_URL="$AWS_ACCOUNT_ID.dkr.ecr.$AWS_DEFAULT_REGION.amazonaws.com/cruddur-python"
echo $ECR_PYTHON_URL
docker pull python:3.10-slim-buster
docker tag python:3.10-slim-buster $ECR_PYTHON_URL:3.10-slim-buster
docker push $ECR_PYTHON_URL:3.10-slim-buster
docker images
docker image rm
```
### Set Path Env
```
export ECR_PYTHON_URL="$AWS_ACCOUNT_ID.dkr.ecr.$AWS_DEFAULT_REGION.amazonaws.com/cruddur-python"
echo $ECR_PYTHON_URL
ENV FLASK_DEBUG=1
#connection_url = os.getenv("PROD_CONNECTION_URL")
connection_url = os.getenv("CONNECTION_URL")

```
## AWS json policy
```
aws iam create-role     --role-name CruddurServiceExecutionRole     --assume-role-policy-document file://aws/policies/service-execution-policy.json
```
### Docker Compose Up
```
docker compose up backend-flask db
```
### Create Role
```
under project folder:
aws iam create-role --role-name CruddurServiceExecutionPolicy --assume-role-policy-document "file://aws/policies/service-assume-role-execution-policy.json"
```
```
aws ecs execute-command  \
--region $AWS_DEFAULT_REGION \
--cluster cruddur \
--task dceb2ebdc11c49caadd64e6521c6b0c7 \
--container backend-flask \
--command "/bin/bash" \
--interactive
```
## Ref
### Cloudscape.


### 
(https://www.envoyproxy.io/)
