# NSHM Core Technology

This section lists the 3rd party services that the NSHM stacks are
based upon.

## Infrastructure services

 - **Amazon Web Services (AWS)** for Cloud services.
 - **Serverless framework** for AWS service management and Contiuous Deployment (CD).
 - **Github** for code version control and CI/CD pipelines using **Github Actions**. 
 - **Pypi** is the usual place where Python libraries are published for public use.
 - Coverage.io.
 
## Development Languages

 - **Python 3** is our primary development language.
   It was selected because our science community end users are comfortable with it and the common python libraries we employ. Also, because the serverless and AWS environments offer good python support.
   NSHM core python libraries are published to PyPI.

 - Java
 - Javascript / Typescript

## Graphql

 - Python: Graphene for schemas
 - Javascript: Apollo for schemas and schema stitching (consolidation).

## Data management

 - AWS S3 object storage
 - AWS DynamoDB table storage
 - AWS Backup
 - AWS ElasticSearch
 - Arrow/Pyarrow for structured datasets ion S3 bucket.

## Version Control

 - Git and github

## Quality Control

 - for python:
    - tox
    - mypy
    - formatting
    - linting
 
## Documentation
 - python + mkdocs