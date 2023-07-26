## Common Infrastructure

NSHM web services use these following core libraries and cloud services across the services layer.


## Cloud services

```mermaid
graph
    classDef nshm stroke:lightgreen, stroke-width:3px
    classDef AWS stroke:orange, stroke-width:3px
    classDef SVC stroke:powderblue, stroke-width:3px    

    l[[lambda]]:::AWS
    S3[( SimpleStorage S3 )]:::AWS
    D[(DynamoDB)]:::AWS
    %%ES[[ElasticSearch]]:::AWS
    GH[Github]:::SVC
    GHA[Github Actions]:::SVC
```

## Python libraries for APIs

```mermaid
graph
   flask
   graphene
   graphql
   boto3
```
## Python libraries for Science

These are the main python libraries used commonly throughtout science application code.

```mermaid
graph
    numpy
    pandas
    geopandas
    shapely
```
## Javascript libraries for APIs
