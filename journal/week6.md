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

## AWS json policy
```
aws iam create-role     --role-name CruddurServiceExecutionRole     --assume-role-policy-document file://aws/policies/service-execution-policy.json
```
## Ref
### Cloudspace.


## Ref
(https://www.envoyproxy.io/)
