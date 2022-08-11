# infrastructure for hosting java webapp on AWS compute cloud

## Cloudformation template for creating the resource stack and making the whole webapp service redeployable

### The main-stack includes:

#### > A VPC block with 3 public and 3 private subnets with relating routing tables
#### > An autoscaling group for deploying instances through a launch template inclusing user data for configuring the application
#### > A remote RDS for providing data access to every instance created along with DynamoDB tables for transient data
#### > A Lambda function along with related roles and policies
#### > A load balancer and a target group pointing to the application
#### > An S3 bucket for object storage by the application along with related roles and policies
#### > KMS keys, aliases and policies for EC2 and RDS encryption
#### > A secure listener for SSL access to the application
#### > Roles, Security groups, policies for securing and consolidating access where needed
#### > Scaling policies along with related alarms
#### > Codedeploy application along with cloudwatch and related policies

Note: Some resources will need additional configurations and existing properties to exist in the AWS account

### Pre-requisite env values:

`export AWS_profile=profile`

`export AWS_REGION=us-east-1`

### Stack creation:

`aws cloudformation create-stack --stack-name main-stack-1 --template-body file://main_stack.yml --parameters ParameterKey=VpcCidrBlock,ParameterValue="10.0.0.0/16" ParameterKey=AMI,ParameterValue="AMI_ID" --capabilities CAPABILITY_NAMED_IAM`

`aws cloudformation create-stack --stack-name CI/CD-roles --template-body file://CI-CD-roles.yml --capabilities CAPABILITY_NAMED_IAM`

### Stack deletion:

`aws cloudformation delete-stack --stack-name main-stack`

### Delete Bucket Objects:

`aws s3 rm s3://BUCKET_NAME --recursive`
