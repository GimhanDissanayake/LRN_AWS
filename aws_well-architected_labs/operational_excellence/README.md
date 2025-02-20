# Intro

Well-Architected tool in the AWS console, AWS Well-Architected Operational Excellence whitepaper.

# Tagging

AWS enables you to assign metadata to your AWS resources in the form of tags 

* manage, search for, and filter resources
* technical tags (e.g., Environment, Workload, InstanceRole, and Name), tags for automation (e.g., Patch Group, and SSMManaged), business tags (e.g., Owner), and security tags (e.g., Confidentiality).

* best practices when using tags:
- Use a standardized, case-sensitive format for tags, and implement it consistently across all resource types
- Consider tag dimensions that support the following:
- Managing resource access control with IAM
- Cost tracking
- Automation
- AWS console organization
- Implement automated tools to help manage resource tags. The Resource Groups Tagging API enables programmatic control of tags, making it easier to automatically manage, search, and filter tags and resources.
- Err on the side of using too many tags rather than too few tags.
- Develop a tagging strategy .

# The impact of Infrastructure as Code
With infrastructure as code, if you can deploy one environment, you can deploy any number of copies of that environment. In this example we have created a Test environment. Later, we will repeat these steps to deploy a Prod environment.

The ability to dynamically deploy temporary environments on-demand enables parallel experimentation, development, and testing efforts. It allows duplication of environments to recreate and analyze errors, as well as cut-over deployment of production systems using blue-green methodologies. These practices contribute to reduced risk, increased operations effectiveness, and efficiency.