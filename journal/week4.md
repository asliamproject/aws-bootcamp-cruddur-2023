# Week 4
## Summary
### I have provision of RDS instance.
```
aws rds create-db-instance \
  --db-instance-identifier cruddur-db-instance \
  --db-instance-class db.t3.micro \
  --engine postgres \
  --engine-version  14.6 \
  --master-username <username>> \
  --master-user-password <password-AWS-USER-POOLS-ID> \
  --allocated-storage 20 \
  --availability-zone ap-southeast-2a \
  --backup-retention-period 0 \
  --port 5432 \
  --no-multi-az \
  --db-name cruddur \
  --storage-type gp2 \
  --publicly-accessible \
  --storage-encrypted \
  --enable-performance-insights \
  --performance-insights-retention-period 7 \
  --no-deletion-protection
```
### Connect to postgres
```
export CONNECTION_URL="postgresql://postgres:password@localhost:5432/cruddur"
gp env CONNECTION_URL="postgresql://postgres:password@localhost:5432/cruddur"
psql $CONNECTION_URL

PROD_CONNECTION_URL = "postgresql://cruddurroot:<password>@cruddur-db-instance.c1suuk4pvdi2.ap-southeast-2.rds.amazonaws.com:5432/cruddur"

NO_DB_CONNECTION_URL=$(sed 's/\/cruddur//g' <<<"$CONNECTION_URL")
psql $NO_DB_CONNECTION_URL -c "DROP database cruddur;"

cruddur=# \x on #Expanded display on
cruddur=# \x auto #Expanded display is used automatically.
cruddur=# SELECT * FROM activities;
```
### Create new activities with a database insert.
replace the hardcoded user_handle value with user name sas under /api/activities route in app.py file.

## Ref:
1.[aws cli rds instance]
(https://docs.aws.amazon.com/cli/latest/reference/rds/)
(https://docs.aws.amazon.com/cli/latest/reference/rds/create-db-instance.html)

2. [psycopg3.2.0](https://www.psycopg.org/psycopg3/docs/)
3. GITPOD_IP=$(curl ifconfig.me)
4. 
```
aws ec2 modify-security-group-rules \
    --group-id $DB_SG_ID \
    --security-group-rules "SecurityGroupRuleId=$DB_SG_RULE_ID,SecurityGroupRule={Description=GITPOD, IpProtocol=tcp,FromPort=5432,ToPort=5432,CidrIpv4=$GITPOD_IP/32}"
```
5. Common PSQL commands:
```
\x on -- expanded display when looking at data
\q -- Quit PSQL
\l -- List all databases
\c database_name -- Connect to a specific database
\dt -- List all tables in the current database
\d table_name -- Describe a specific table
\du -- List all users and their roles
\dn -- List all schemas in the current database
CREATE DATABASE database_name; -- Create a new database
DROP DATABASE database_name; -- Delete a database
CREATE TABLE table_name (column1 datatype1, column2 datatype2, ...); -- Create a new table
DROP TABLE table_name; -- Delete a table
SELECT column1, column2, ... FROM table_name WHERE condition; -- Select data from a table
INSERT INTO table_name (column1, column2, ...) VALUES (value1, value2, ...); -- Insert data into a table
UPDATE table_name SET column1 = value1, column2 = value2, ... WHERE condition; -- Update data in a table
DELETE FROM table_name WHERE condition; -- Delete data from a table
```

