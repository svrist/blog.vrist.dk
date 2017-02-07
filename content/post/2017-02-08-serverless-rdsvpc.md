+++
date = "2017-02-08"
title = "Configuring VPC and RDS via Cloudformation for AWS Lambda"
categories = ["English", "Tech"]
tags = ["aws", "rds", "lambda", "cloudformation", "sqlalchemy", "vpc"]
draft = false

+++

[I have outlined the overall "project"]({{< relref "2017-02-06-serverless.md" >}})
 and here is my notes on the RDS + VPC challange:

#### Setting up RDS (and VPC) via CloudFormation

[The Serverless Framework](https://serverless.com/) has fields to include
[verbatim CloudFormation template data](https://serverless.com/framework/docs/providers/aws/guide/resources/)
- but I found myself unable to figure out how to get the resulting connection
information into my lambda function without running CloudFormation api calls
to get outputs of a given CloudFormation stack either as plugin that
[repackages the zipfile of the lambda after the CloudFormation stack has
executed or as seperate standalone stack where values are then available when
the serverless framework
deploys](http://forum.serverless.com/t/can-i-access-outputs-from-custom-resources-as-variables-in-serverless-yml/508).
Both as [cross-stack references](https://aws.amazon.com/blogs/aws/aws-cloudformation-update-yaml-cross-stack-references-simplified-substitution/)
(VPC info) and as CloudFront outputs which
could be dumped to a python or json file and loaded at runtime of the lambda
function.
I decided on the latter approach and effective added in another step before
doing `serverless deploy`

```
aws cloudformation update-stack \
    --stack-name something-database \
    --template-body ....  \
    --parameters ...  # [1][2]
aws cloudformation describe-stacks \
    --stack-name something-database > db.out.json # [3]
serverless deploy --stage mystage
```
<sub> `[1]`[I ended up doing it via boto3 and
python](https://gist.github.com/svrist/73e2d6175104f7ab4d201280acba049c)</sub><br/>
<sub>`[2]`: I based my template of [something I found
online](http://www.stojanveselinovski.com/blog/2016/01/12/simple-postgresql-rds-cloudformation-template/)
and augmented with `Outputs` for my needs</sub><br/>
<sub>`[3]`: [I also ended up doing that via boto3 and python](https://gist.github.com/svrist/d03f0dffefb215f1b8843176e9f48d59)</sub>

Doing it this way meant that I could write
```
vpc:
  securityGroupIds:
    - {"Fn::ImportValue": "db-${self:custom.stage}-SecurityGroupID"}
  subnetIds:
    - {"Fn::ImportValue": "db-${self:custom.stage}-SubnetA"}
    - {"Fn::ImportValue": "db-${self:custom.stage}-SubnetB"}
    - {"Fn::ImportValue": "db-${self:custom.stage}-SubnetC"}
```
in my `serverless.yml` and do something like the `json.load` in
[handler.py](https://gist.github.com/svrist/17bcc48d4cf2a86ea1391ae46db46b81#file-handler-py-L15)
With current versions of serverless and AWS Lambda it should also be possible
to [add the values to the environment via a yaml
load](https://serverless.com/framework/docs/providers/aws/guide/functions/#environment-variables)

##### VPC considerations

With regards to VPC it's worth noticing that when you add your Lambdas to
custom VPCs internet access, S3 access is no longer implictly available.
Specifically I met some gotchas around S3 VPC Endpoint configuration along
with Security Groups and VPC and general access from Lambda to the RDS
network-wise. The main result is this:

{{< gist svrist 6d15e48af94515f10ef828aad5e14aa1 >}}


