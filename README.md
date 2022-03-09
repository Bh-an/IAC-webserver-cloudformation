# infrastructure
Cloudformation templates for VPC creation

Pre-requisite env values:

`export AWS_profile=demo`

`export AWS_REGION=us-east-1`

Stack creation:

`aws cloudformation create-stack --stack-name full-test --template-body file://csye6225-infra.yml --parameters ParameterKey=VpcCidrBlock,ParameterValue="10.0.0.0/16" ParameterKey=AMI,ParameterValue="ami-011a0aa2aa8d7201b"`

Stack deletion:

`aws cloudformation delete-stack --stack-name full-test`
