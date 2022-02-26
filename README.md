# infrastructure
Cloudformation templates for VPC creation

Pre-requisite env values:

`export AWS_profile=demo`

`export AWS_REGION=us-east-1`

Stack creation:

`aws cloudformation create-stack --stack-name test-vpc-demofinal --template-body file://csye6225-infra.yml --parameters ParameterKey=VpcCid
rBlock,ParameterValue="10.0.0.0/16"`
