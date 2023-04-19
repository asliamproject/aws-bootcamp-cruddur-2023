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

Connect to command
```
aws ecs execute-command  \
--region $AWS_DEFAULT_REGION \
--cluster cruddur \
--task 1a260bca90c74e8286eded00876af667 \
--container backend-flask \
--command "/bin/bash" \
--interactive
```
list tasks
```
aws ecs list-tasks --cluster cruddur
```

###
```
docker build \
--build-arg REACT_APP_BACKEND_URL="cruddur-alb-1251172003.ap-southeast-2.elb.amazonaws.com:4567" \
--build-arg REACT_APP_AWS_PROJECT_REGION="$AWS_DEFAULT_REGION" \
--build-arg REACT_APP_AWS_COGNITO_REGION="$AWS_DEFAULT_REGION" \
--build-arg REACT_APP_AWS_USER_POOLS_ID="ap-southeast-2_JVO6xcApv" \
--build-arg REACT_APP_CLIENT_ID="5asnsktofp1k8rbsa47am21ms4" \
-t frontend-react-js \
-f Dockerfile.prod \
.
```
## Ref
### Cloudscape.


### 
(https://www.envoyproxy.io/)

### Install Session Manager Plugin
(https://docs.aws.amazon.com/systems-manager/latest/userguide/session-manager-troubleshooting.html#plugin-not-found)
(https://docs.aws.amazon.com/systems-manager/latest/userguide/session-manager-working-with-install-plugin.html#install-plugin-linux)
