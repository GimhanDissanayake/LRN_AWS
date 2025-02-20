1. Create AWS Account for a new project
  a. Set alias account name
  b. Set SCP - *does not apply to management account
  c. Do not deploy resources into Management Account
  d. Enable IAM Accsss to Billing Informations
  e. Set billing preference
    1. Receive Bill by email
    2. Receive free tier usage alert
  f. Set billing alert in N.verginia region

2. AWS Orgnization
  a. Management Group(Root)
  b. OU
  c. SCP (Control API Actions)
  d. Consolidated bill
  e. AWS SSO using on-prem directory
  f. CloudTrail in management account and apply to members
  g. OrganizationAccountAccessRole is created on new accounts(this role can be assumed by any user with the sts:AssumeRole permissions)
