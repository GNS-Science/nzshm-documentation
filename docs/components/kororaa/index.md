
# Introducing Kororaa and its Application API gateway

Th NSHM public web application (aka **Kororaa**) has an **Applicaton API gateway** which consolidates NSHMs functional APIs using graphql stitching.


```mermaid
graph TD
    classDef nshm stroke:lightgreen, stroke-width:3px
    classDef AWS stroke:orange, stroke-width:3px
    classDef SVC stroke:powderblue, stroke-width:3px    

    kororaa["Kororaa
     nshm.gns.cri.nz"]:::nshm
    apigw["Graphql API gateway
     nshm-kororaa-prod-apigw"]:::AWS
     
    apis["NSHM graphql APIs
     Toshi, solvis, etc"]:::nshm
    app_bucket["Application S3 bucket
     s3::nshm-koraraa-prod-
    "]:::AWS

    kororaa -.-> |uses| apigw -.-> |aggregates| apis
    kororaa --- |is served from| app_bucket

    %% GHA[Github Actions]:::SVC
```