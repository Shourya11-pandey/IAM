🔐 IBM Cloud IAM + Object Storage: Secure Access Control Simulation
A hands-on simulation demonstrating secure, role-based access to IBM Cloud Object Storage (COS) using Identity and Access Management (IAM) principles. Learn how cloud teams protect resources by controlling access through Access Groups, IAM Roles, and optional automation using Service IDs.

🎯 Objective
To build and test a secure access control system in IBM Cloud using:

Multiple IBM Cloud accounts (users)
IAM access groups with scoped permissions
Roles: Viewer, Editor, and Manager
Optional automation via Service IDs
🧰 Tools & Services
Tool / Service	Function
IBM Cloud Console	Main interface to configure services
IBM Cloud Object Storage	Stores data in secure, scalable cloud buckets
IBM IAM	Controls access to cloud services
Access Groups	Apply consistent permissions to user sets
Resource Groups	Organize resources logically
Service IDs (optional)	Automate access via programmatic credentials
🚦 Step-by-Step Setup Guide
1️⃣ Create an IBM Cloud Object Storage Instance
Log into your IBM Cloud Account.
In the top navigation, click Catalog.
Search for "Cloud Object Storage".
Click on Cloud Object Storage, then click Create.
Choose your location, pricing plan (use Lite for free), and resource group (default or custom).
Click Create to deploy your COS instance.
2️⃣ (Optional) Create a New Resource Group
Resource Groups help segment environments (e.g., Dev, Test, Prod).

From the left sidebar, go to Manage → Account → Resource Groups.
Click Create Resource Group.
Provide a name like Project-AccessControl-RG.
Click Create.
3️⃣ Create Access Groups
Access Groups define what a set of users can do.

Navigate to IAM → Access Groups.
Click Create.
Create the following groups:
ViewerGroup – for users with read-only access.
EditorGroup – for users who can upload/delete objects.
ManagerGroup – for users with full COS control.
Save each group after naming.
4️⃣ Assign IAM Roles to Access Groups
Define what each group can do on your COS instance.

Go to IAM → Access Groups.
Select a group (e.g., ViewerGroup).
Click Access Policies → Assign access.
Choose:
Service: Cloud Object Storage
Resource Type: Object Storage instance
Scope: Specific instance or resource group
Role:
ViewerGroup → Viewer
EditorGroup → Writer
ManagerGroup → Manager
Repeat this for all three groups.
5️⃣ Invite Users and Assign to Access Groups
Go to IAM → Users → Invite Users.
Enter the email addresses of the users you want to invite.
Under Access Groups, assign them to:
ViewerGroup
EditorGroup
ManagerGroup
Send the invitation. Users will receive an email to join IBM Cloud.
6️⃣ Create a Bucket in Your COS Instance
Navigate to your Cloud Object Storage service.
Click on the Buckets tab.
Click Create Bucket.
Fill in:
Bucket Name: test-bucket
Location: Closest region (e.g., us-south)
Storage Class: Smart Tier or Standard
Resiliency: Choose based on needs (e.g., Regional)
Click Create.
7️⃣ Log in as Users and Test Permissions
Each user (from ViewerGroup, EditorGroup, ManagerGroup) should now:

Log in to IBM Cloud using their email/password.
Navigate to Resource List → Storage → Cloud Object Storage.
Open the test-bucket.
Try performing actions based on their roles:
Action	Viewer	Editor	Manager
View list of buckets	✅ Allowed	✅ Allowed	✅ Allowed
Upload file to bucket	❌ Denied	✅ Allowed	✅ Allowed
Delete object from bucket	❌ Denied	✅ Allowed	✅ Allowed
Delete bucket	❌ Denied	❌ Denied	✅ Allowed
View/Edit lifecycle or CORS	❌ Denied	❌ Denied	✅ Allowed
Check if the system correctly allows or denies actions.

8️⃣ (Optional) Use Service IDs for Automation
Go to IAM → Service IDs → Create.
Name the service ID (e.g., cos-automation-id).
Assign it to a group (e.g., EditorGroup or ManagerGroup).
Create an API Key.
Use this key for CLI/API-based access to COS:
Upload/delete objects
Automate testing
✅ Access Capability Matrix
Task	Viewer	Editor	Manager
🔍 View Buckets	✅	✅	✅
📤 Upload Files	❌	✅	✅
❌ Delete Objects	❌	✅	✅
🪣 Create/Delete Buckets	❌	❌	✅
⚙️ View/Edit Lifecycle/CORS	❌	❌	✅
🧪 Outputs Observed
✔️ Viewer was restricted to read-only access.
✔️ Editor was able to upload/delete but not manage settings.
✔️ Manager had full access to buckets and configurations.
❌ Unauthorized actions were properly blocked.
📋 Access logs were viewable under IAM → Activity Tracker (if enabled).
🎓 Key Takeaways
IAM roles simplify complex permission models in IBM Cloud.
Access Groups enable scalable and manageable access policies.
Clear role definitions prevent accidental or malicious access.
Service IDs help automate secure workflows.
📌 Conclusion
This simulation proves how IBM Cloud IAM empowers teams to secure cloud storage using clear, enforceable role-based policies. It mirrors best practices in enterprise-grade cloud security — scoped permissions, minimal privilege, and group-based control.

🚀 Future Enhancements
🔍 Enable Activity Tracker for full audit logging.
🤖 Integrate with Watson AI for intelligent file analysis.
⚙️ Automate setup via Terraform or IBM Cloud CLI.
📊 Visualize access metrics and user activity.
🔐 Add custom roles for finer-grained permissions.
✍️ Created by: Shourya 
