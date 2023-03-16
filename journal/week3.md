# Week 3
## Summary
### use the following command to change/update AWS Cognito email password:
gitpod /workspace $ aws cognito-idp admin-set-user-password --username jiezheng --password Testing1234! --user-pool-id ap-southeast-2_gFNNzdppM --permanent

username email: kapoji6604@luxeic.com
password: Testing1234!

### I have setup Cognito User Pool.

### I have implemented User Signin and Signup page.

### I have implemented Customer Confirmation and Recovery page.

### I have implemented JWT token server side.

## Ref:
1.
What is JWT API authentication?
To authenticate a user, a client application must send a JSON Web Token (JWT) in the authorization header of the HTTP request to your backend API. API Gateway validates the token on behalf of your API, so you don't have to add any code in your API to process the authentication.

2. [Verifying a JSON web token](https://docs.aws.amazon.com/cognito/latest/developerguide/amazon-cognito-user-pools-using-tokens-verifying-a-jwt.html)

3. [JS library for verifying JWTs signed by Amazon Cognito, and any OIDC-compatible IDP that signs JWTs with RS256, RS384, and RS512](https://github.com/awslabs/aws-jwt-verify)

4. [Social networking, back in your hands](https://fediverse.info/)
### AWS Amplify