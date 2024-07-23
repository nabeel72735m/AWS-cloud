##Note - first we should connect the git to our local terminal
 to connect the git to our terminal the below command is used
 ```
 git config --global user.name Shaik Nabeel
git config --global user.email nabeel72735m@gmail.com
```
to check we will be useing this command
```
git config --list

```


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
2 . this commans is used to delete the vpcs through cli
```
aws ec2 delete-vpc --vpc-id <vpc-id>
```
  ### lab:

  i will be using the abouve command to create vpcs
  output:
  ```
  {
    "Vpc": {
        "CidrBlock": "10.0.0.0/16",
        "DhcpOptionsId": "dopt-089b1f160802476c0",
        "State": "pending",
        "VpcId": "vpc-00d8b72f9bfe58d6c",
        "OwnerId": "481724031218",
        "InstanceTenancy": "default",
        "Ipv6CidrBlockAssociationSet": [],
        "CidrBlockAssociationSet": [
            {
                "AssociationId": "vpc-cidr-assoc-067aff2310f6415a3",
                "CidrBlock": "10.0.0.0/16",
                "CidrBlockState": {
                    "State": "associated"
                }
            }
        ],
        "IsDefault": false,
        "Tags": [
            {
                "Key": "Name",
                "Value": "MyVpc"
            }
        ]
    }
}

```


### now i will create some github action
to create github action we will be creating the file
the command is 

```
pwd 
ls -a 
mkdir -p .github/workflows

```


### For creating aws actions
example : in our local terminal if we want lo connect aws we need cli in that 
we will connect cli with this command by using access and secret access key
```
aws configure
```


roughwork:
```

name: GitHub Actions Demo
run-name: ${{ github.actor }} is testing out GitHub Actions 🚀
on: [push]
jobs:
  Explore-GitHub-Actions:
    runs-on: ubuntu-latest
    steps:
      - run: echo "🎉 The job was automatically triggered by a ${{ github.event_name }} event."
      - run: echo "🐧 This job is now running on a ${{ runner.os }} server hosted by GitHub!"
      - run: echo "🔎 The name of your branch is ${{ github.ref }} and your repository is ${{ github.repository }}."
      - name: Check out repository code
        uses: actions/checkout@v4
      - run: echo "💡 The ${{ github.repository }} repository has been cloned to the runner."
      - run: echo "🖥️ The workflow is now ready to test your code on the runner."
      - name: List files in the repository
        run: |
          ls ${{ github.workspace }}
      - run: echo "🍏 This job's status is ${{ job.status }}."
      - uses: aws-actions/configure-aws-credentials@v2
        with:
          aws-access-key-id: ${{ secrets.AWS_ACCESS_KEY_ID }}
          aws-secret-access-key: ${{ secrets.AWS_SECRET_ACCESS_KEY }}
          aws-region: us-east-1
      - run: aws ec2 create-vpc  --cidr-block 10.0.0.0/16  --tag-specifications 'ResourceType=vpc,Tags=[{Key=Name,Value=MyVpc}]'
      - run: aws ec2 describe-vpcs
````  
#### the abouve code is used to create vpc through cli with githuib action.