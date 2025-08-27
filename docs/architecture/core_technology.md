# NSHM Core Technology

This section discusses the software technology used in the NSHM project.

## Infrastructure services

 - **Amazon Web Services (AWS)** for Cloud services.

 - **Github** for code version control and CI/CD pipelines using **Github Actions**. 
 - **Pypi** is the usual place where Python libraries are published for public use.
 - **codecov.io** helps us report on code coverage.
 
## Development Languages

Our main drivers in selecting sotware languages are:

 - ease of use for the wider science community,
 - talent pool - can we get access to extra developers when necessary,
 - good support across the common compute platforms,
 - compatablity with other projects we need to collaborate with (GEM, USGS).

With these considerations, we have the following:

 - **Python 3** is our primary development language.
   Python is used widely in our science community, as are many of the python libraries we used. Since we want to share our sofware with the community it makes sense to delivey this in python. Our main NSHM python libraries are published to PyPI.
 - **Java** is mainly used for USGS collaboration.
 - **Javascript** and **Typescript** are used in our web applications, and for their API gateways. These are chosen because of the frameworks available, and their wide coommunity support.

## Frameworks

 - **Apollo** for schemas and schema consolidation (javascript)
 - **Graphene** for graphql schema microservices (python)
 - **Material UI** for Web application styinng (typescript/CSS)
 - **Serverless framework** for AWS service management and Contiuous Deployment (CD).
 - **React** for the web application logic (typescript)
 - **Arrow** for dataset management (python + pyarrow) 

## Data management

 - AWS S3 object storage
 - AWS DynamoDB table storage
 - AWS Backup
 - AWS ElasticSearch
 - Arrow/Pyarrow for structured datasets in S3 bucket.

## Version Control

 - Git and github

## Quality Control

 - for python:
    - tox
    - mypy
    - black
    - linting
 
## Documentation
 - python + mkdocs