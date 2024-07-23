##Note - first we should connect the git to our local terminal

## This is the github repo to shoecase my work on Aws
## Chapter1 : Aws cli/cloudformation
 
 in this chapter i will create the labs to show the aws
 resource creation through aws cli and cloudformation.

1. This command is used to create vpc through aws cli
```
   aws ec2 create-vpc \
    --cidr-block 10.0.0.0/16 \
    --tag-specifications 'ResourceType=vpc,Tags=
    [{Key=Name,Value=MyVpc}]'
``` 