#### AWS Account:
- Always provide alternate contact for billing, operation and security in account setting
- Activate IAM Access to billing information in account setting so all IAM user with attached policy can access the billing information without this they can't access even permission attached.
- Always enable MFA for account from IAM to secure your account. with just username and password anyone can fake your identity, so with added MFA(physical/application) it's harder to fake.
	- Something you know (username and password)
	- Something you have (MFA code)
- In Billing enable invoice delivery preference by email to get invoice pdf on email
- Also enable alert preferences
- Define budgets when needed to manage account budget so that you get alert when certain threshold hit. `Billing >> preference`
- Root user has unrestricted access to AWS account
- Only give permissions required to the users or apps using IAM
- Every AWS account has it's own IAM service and database, IAM is global service.
- IAM as a service can do as much as root user, billing limitation.
- IAM has 3 different services
	- Users: represent humans or applications
	- Group: Collection of related users
	- Role: AWS services or external access (give EC2 access to AWS account/service (S3))
- Policy is used to Allow or deny access to the services. It can be attached to all top IAM services.
- ID provider --> Authenticate --> Authorize
- No cost for IAM, Global service, It control only it's identities, No direct control on external accounts, IAM let's you use Identity Federation and MFA.
- User can have max 2 active or inactive access keys
- configure named profile in you local aws CLI setup so you can use multiple accounts
  `aws configure --profile iamadmin-general`
- and to use particular account use `aws s3 ls --profile iamadmin-general`

#### AWS Fundamental

Region:

Edge Locations:
- Edge locations are located near to the user
- It's used to 