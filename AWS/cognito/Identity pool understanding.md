
## **What is an Identity Pool?**

- **Cognito User Pool** = _manages user authentication (signup/login).
- **Cognito Identity Pool** = _gives authenticated users **temporary AWS credentials** (IAM roles)._  
    → These credentials allow them to access **other AWS services directly** (like S3, DynamoDB, etc.).




### **AWS Console (UI)**

Best for visual learners and initial testing.

1. Go to [Cognito in AWS Console](https://console.aws.amazon.com/cognito/)
    
2. Click **“Federated Identities”**
    
3. Click **“Create new identity pool”**
    
4. Give it a name (e.g., `MyAppIdentityPool`)
    
5. ✅ Enable access to **unauthenticated identities** (optional)
    
6. Under **Authentication providers**:
    
    - Choose **Cognito** (the tab)
        
    - Add:
        
        - **User Pool ID**
            
        - **App Client ID**
            
7. Click **Create Pool**
    

➡️ AWS **automatically creates IAM roles**:

- One for **authenticated users**
    
- One for **unauthenticated users** (if enabled)



