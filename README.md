# infrastructure
Cloudformation templates for VPC creation

Pre-requisite env values:

`export AWS_profile=demo`

`export AWS_REGION=us-east-1`

Stack creation:

`aws cloudformation create-stack --stack-name new-test --template-body file://CLOUDFORMATION.yml --parameters ParameterKey=VpcCidrBlock,ParameterValue="10.0.0.0/16" ParameterKey=AMI,ParameterValue="AMI_ID" --capabilities CAPABILITY_NAMED_IAM`

Stack deletion:

`aws cloudformation delete-stack --stack-name new-test`

Delete Bucket Objects:

`aws s3 rm s3://BUCKET_NAME --recursive`
