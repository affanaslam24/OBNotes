Android/Web App
      ↓
   Login (Cognito)
      ↓
Access Token (JWT)
      ↓
   API Gateway
      ↓
Authorizer (Cognito JWT check)
      ↓
   AWS Lambda
      ↓
   DynamoDB / S3 / RDS / etc.

- Use **Cognito** for authentication
- Send an **access token (JWT)** to **API Gateway**
- API Gateway will verify the token
- If valid, it will invoke **Lambda**

## Step-by-Step Setup

### 1️⃣ **Create a Cognito User Pool**

In AWS Console:
- Go to **Cognito > User Pools > Create Pool**
- Add email/password-based sign-in
- Allow self sign-up or admin-only, based on your use case
- Get the **User Pool ID** and **App Client ID**



i havent implemented this in practical, but will do later on.


---


can i just use user pool if i dot need to access any aws resource?


A **User Pool** is mainly for:

|Function|Provided by User Pool?|
|---|---|
|User sign up / sign in|✅ Yes|
|User directory|✅ Yes|
|Email/phone verification|✅ Yes|
|Multi-Factor Auth (MFA)|✅ Yes|
|Password reset / change|✅ Yes|
|JWT token issuance|✅ Yes (`ID`, `Access`, `Refresh`)|
|Custom attributes|✅ Yes|
|User groups / roles|✅ Yes (User Pool Groups)|
|App-only auth|✅ Yes|


Say you're building a **blogging app** or a **chat app**, and:

- Users can log in
    
- Backend API handles all logic and access to AWS resources
    
- The **frontend just calls API Gateway** (which talks to Lambda, DynamoDB, etc.)
    

In this case, **you don't need an Identity Pool at all**.

You would:

1. Use User Pool to authenticate user
    
2. Send the JWT (ID token or Access token) in `Authorization` header to your API Gateway
    
3. API Gateway checks token validity via Cognito Authorizer
    
4. Lambda runs and interacts with resources like S3, DynamoDB using its **own IAM role**



