+++
date = "2017-02-06"
title = "Amazon Lambda, Serverless Framework, Python and RDS"
categories = ["English", "Tech"]
tags = ["aws", "rds", "lambda", "cloudformation", "sqlalchemy"]

+++

I've been playing around with
[the Serverless Framework](https://serverless.com/) for setting up a simple
API which fetches either one piece of data from a database or a list of
things.

### Setup

I decided on using [Amazon RDS](https://aws.amazon.com/rds/) PostgreSQL as
the database and figured that would be a pretty standard thing to do but
within the Serverless framework it's apparently not done that often.
[AWS has got a
tutorial](http://docs.aws.amazon.com/lambda/latest/dg/vpc-rds.html) so it's
not completely impossible.

### Challenges

- [Connection pooling / or
  not](https://forums.aws.amazon.com/thread.jspa?threadID=216000)
  As the lambdas potentially could scale indefinitely and a standard RDS
  instance is just running like any other normal PostgreSQL database which
  allows a finite amount of connections. I decided to "fix it when it becomes
  a problem".
- How to install psycopg in a Python Lambda?
- [VPC access](https://aws.amazon.com/vpc/) (or publicly available database)?
  Preferably via  [the Serverless Framework](https://serverless.com/) or at
  least via cloudformation

I have create a post for each of the latter two challenges:

- [Serverless and psycopg]({{< relref "2017-02-07-serverless-psycopg.md" >}})
- [Serverless and RDS+VPC]({{< relref "2017-02-08-serverless-rdsvpc.md" >}})
