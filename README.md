 Role-Based Access Control (RBAC) Using AWS IAM for EC2 Management
Youtube link : https://youtu.be/JsGi165zboQ
This repository demonstrates a secure, role-based access control (RBAC) configuration in AWS using IAM. The project provides a practical setup where one IAM user receives EC2 privileges via a direct policy, while S3 access is granted only through a group. This approach ensures controlled, segregated, and purpose-driven permissions.
 Objective
To implement a secure AWS IAM configuration where:
- A user receives **EC2 access through a user-attached policy**
- The same user receives **S3 access only through IAM group membership**
🏗 Architecture Overview
| Component | Access Type | Permission Source |
|-----------|-------------|------------------|
| **User128** | EC2 Management | `AmazonEC2FullAccess` (Direct Policy) |
| **User128** | S3 Bucket Access | `AmazonS3FullAccess` (Through Group `S3Group`) |
 This model demonstrates **principle of least privilege** and **policy segregation**.
 🛠 Implementation Steps
1️ Create IAM User (Without Permissions)
- Go to **IAM → Users → Create user**
- Username: `User128`
- Enable AWS Console Password Access
  - Do **not** assign permissions during user creation
 Create IAM Group for S3 Permissions
- Navigate to **IAM → User groups → Create group**
- Group Name: `S3Group`
- Attach Policy: `AmazonS3FullAccess`
- Add `User128` to this group
 Assign EC2 Permissions Directly to User
- Go to **IAM → Users → User128 → Permissions**
- Click **Add permissions**
- Select **Attach policies directly**
- Choose: `AmazonEC2FullAccess`
 Validate Access (Login as User128)
- Sign in using the IAM sign-in URL
- Confirm:
   EC2 Console is accessible  
  S3 Console is accessible  
  Other services (not permitted) remain locked
   Security Recommendations
This project demonstrates:
- Role-based access governance using IAM
- Separation of privilege through users and groups
- Real-world security practices for AWS accounts
- Deployment of RBAC without over-privileged users

