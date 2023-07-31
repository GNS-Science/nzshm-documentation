## The Graphql Application API gateway pattern
There are two API layers involved for the main NSHM web application (Kororaa) . The pattern is commonly known as  a `microservice` architecture, where the lower layer consists of domain-specific services that are then composed into collections by an API gateway. THe Kororaa application is required to communicate with a single API gateway, which in turn passes on call to the relevant API microservice(s). Try google [or here](https://microservices.io/index.html) for information about this style of services organisation.

```mermaid
graph TD
    classDef nshm stroke:lightgreen, stroke-width:3px
    classDef AWS stroke:orange, stroke-width:3px
    classDef SVC stroke:powderblue, stroke-width:3px
    classDef note stroke:black, stroke-width:1px
    
    K["Kororaa web app
    nshm-test.gns.cri.nz"]:::nshm
    NB["https://nshm-api-test.gns.cri.nz/kororaa-app-api/graphql"]:::note 
    subgraph GW["API Gateway layer"]
        A["API Gateway:
        test-nshm-kororaa-apigw (4ra58fifn3)"]:::AWS
        F["lambda:
        nshm-kororaa-apigw-test-app"]:::AWS
    end

    subgraph SUP["graphql microservices layer"]
        direction LR

        K-API[kororaa-graphql-api]:::nshm
        S-API[solvis-graphql-api]:::nshm
        T-API[nshm-toshi-api]:::nshm               
    end
    K -.-|graphql query| NB -.-> A -->|path: kororaa-app-api/graphql| F 
    F --> S-API
    F --> K-API
    F --> T-API 

```

The NSHM service APIs are all using [graphql standard](https://graphql.org/). This means that the API gateway can also provide [schema stitching](https://the-guild.dev/graphql/stitching/docs) to improve flexibilty and efficiencies that benefit the client application.

In the Kororaa APP API Gateway example shown above we have a web application client which communicates with a single API Gateway endpoint. This APIGW in turn communicates with whichever domain API services are required to service the application functions.

 - [Kororaa application API Gateway](/nzshm-documentation/components/nshm_kororaa_apigw/)

 - [solvis-graphql-api](/nzshm-documentation/components/solvis_graphql_api)


## Combined model


```mermaid
graph TD
    classDef nshm stroke:lightgreen, stroke-width:3px
    classDef AWS stroke:orange, stroke-width:3px
    classDef SVC stroke:powderblue, stroke-width:3px
    classDef note stroke:black, stroke-width:1px
    
    K["Kororaa web app
    nshm-test.gns.cri.nz"]:::nshm
    NB["https://nshm-api-test.gns.cri.nz/kororaa-app-api/graphql"]:::note 


    T["Tui web app
        tui-test.gns.cri.nz"]:::nshm
    NB2["https://nshm-api-test.gns.cri.nz/tui-app-api/graphql"]:::note 


    K -.-|graphql query| NB -.-> A
    T -.-|graphql query| NB2 -.-> B

    subgraph GW["API Gateway layer"]
        A["kororaa API Gateway:
        test-nshm-kororaa-apigw (4ra58fifn3)"]:::AWS
        F["lambda:
        nshm-kororaa-apigw-test-app"]:::AWS

        B["Tui API Gateway:
        test-nshm-tui-apigw ()"]:::AWS
        F2["lambda:
        nshm-tui-apigw-test-app"]:::AWS

        A -->|path: kororaa-app-api/graphql| F 
        B -->|path: tui-app-api/graphql| F2 

    end

    subgraph SUP["graphql microservices layer"]
        %% direction LR

        K-API[kororaa-graphql-api]:::nshm
        S-API[solvis-graphql-api]:::nshm
        T-API[nshm-toshi-api]:::nshm               
    end
    
    F -.-> SUP
    F2 -.-> SUP

```