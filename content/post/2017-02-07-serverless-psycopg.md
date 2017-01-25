+++
date = "2017-02-07"
title = "Running Python with Psycopg2 on AWS Lambda"
categories = ["English", "Tech"]
tags = ["aws", "rds", "lambda", "psycopg2", "sqlalchemy", "python"]
draft = true

+++

[I have outlined the overall "project"]({{< relref "2017-02-06-serverless.md" >}})
 and here is my notes on the psycopg2 challenge:

##### Installing [Psycopg](http://initd.org/psycopg/) and setting up logging
In general - you need to include all dependencies when deploying the Lambda. I
decided on an approach that included a "vendored" directory and do sys.path
mangling.

```
.
├── content
│   ├── common.py
│   ├── __init__.py
│   └── import.py
├── database -> ../database
├── handler.py
├── __init__.py
├── lambdahelper.py
├── serverless.yaml
└── vendored
    ├── psycopg2
....
    ├── contextlib2.py
....
    ├── dateutil
etc
```
In my git repo I added included the vendored library of psycopg2 and install
the rest of the needed content of vendored with `pip -t` during deployment.
The special case of psycopg turns out to
[be](http://stackoverflow.com/questions/36607952/using-psycopg2-with-lambda-to-update-redshift-Python)
[needed](https://forums.aws.amazon.com/thread.jspa?threadID=217796). I used the version from
https://github.com/jkehler/awslambda-psycopg2. TLDR is:

- No PG libraries on the AMI that runs lambdas
  (http://docs.aws.amazon.com/lambda/latest/dg/current-supported-versions.html)
- You can spin up such an api up and build the C libraries statically linked
  and include them along the psycogp2 code when zipping the lambda.
  - Or checkout
  [that repo](https://github.com/jkehler/awslambda-psycopg2) and include
  that - if you trust that code.

<sub>And the same for any library depending on C extensions that isn't already
in the lambda AMI</sub>

Then, when running the lambda, to tell the Python code where I left it's third
party dependcies I do some sys.path wrangling:

{{< gist svrist f77760996669475d922d57cc9e77c390 >}}

Which means my handler.py must, before any other external dependencies,
`import _pathmangle`

In order to get decent
[logging](http://docs.aws.amazon.com/lambda/latest/dg/python-logging.html)
in cloudwatch  I also include a "lambdahelper.py" that setups up the normal
python logging with a [Serverless Framework](https://serverless.com/) friendly
format and silences the excessive boto logging.

{{< gist svrist 92314c495310cbef1bd02ff95a474214 >}}

Put together in a handler.py it looks like this:

{{< gist svrist 17bcc48d4cf2a86ea1391ae46db46b81 >}}

Before running `serverless deploy` I then need to make sure my `pip`
dependencies are installed and uptodate:
```
pip install -t vendored -r requirements.txt
```
