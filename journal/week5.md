# Week 4
## Summary
### Complete DynamoDB Utility Script such as Setup Dynomodb schema_load, list tables, seed data.
### AWS CLI Command LIST COGNITO USERS 
hard code in /backend-flask/bin/ddb/patterns/get-conversations
message_group_uuid = "5ae290ed-55d1-47a0-bc6d-fe2bc2700399"
```
./bin/db/create
./bin/db/schema-load
./bin/db/seed
./bin/ddb/patterns/list-conversations
./bin/ddb/patterns/get-conversations
```

```
$ aws cognito-idp list-users --user-pool-id=<ap-southeast-2_USER POOL ID>
```

```
./bin/cognito/list-users
env | grep COGNITO
```
### Create Lambda function for DynamoDB messaging stream
### Create Stream:
create table
```
$gitpod /workspace/aws-bootcamp-cruddur-2023/backend-flask (main) $ ./bin/ddb/schema-load prod
```
AWS DynamoDB>Tables>Exports and streams>DynamoDB stream details>Turn on>New image>Turn on stream
## Ref:
1. Boto3 Docs.
(https://boto3.amazonaws.com/v1/documentation/api/latest/index.html)