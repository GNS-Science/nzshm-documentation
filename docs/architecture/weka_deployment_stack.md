## Weka web application stack

The **Weka App** supercedes the original TUI (Toshi UI) application with a similar but modernised architecture. 
It's used primarily by the CWG team and NSHM scientists
involved in running and evaluating experimental results from the NSHM CWG [Scientific Process](./science_process/).

## Custom components

These components are developed and supported by the Compute Working Group team.

 - [Weka wep application ](/nzshm-documentation/components/weka/) is the Weka UI.
    
    **Github:** [GNS-Science/weka](https://github.com/GNS-Science/weka).

 - [Weka API Gateway](/nzshm-documentation/components/nshm_weka_apigw/) is the application API for Weka.
    
    **Github:** [GNS-Science/nshm-weka-apigw](https://github.com/GNS-Science/nshm-weka-apigw).

 - [solvis-graphql-api](/nzshm-documentation/components/solvis_graphql_api) is a graphql API wrapping the [solvis](https://github.com/GNS-Science/solvis) library. 
    
    **Github:** [GNS-Science/solvis-graphql-api](https://github.com/GNS-Science/solvis-graphql-api). Used by the Rupture Map explorer UI component.

 - [nshm-model-graphql-api](/nzshm-documentation/components/nshm-model-graphql-api) is a graphql API wrapping the nzshm-model library. 
    
    **Github:** [GNS-Science/nshm-model-graphql-api](https://github.com/GNS-Science/nshm-model-graphql-api).

 - [nshm-toshi-api](/nzshm-documentation/components/nshm_toshi_api) is a graphql API managing the NSHM experimental artefacts.
    
    **Github:** [GNS-Science/nshm-toshi-api](https://github.com/GNS-Science/nshm-toshi-api).

The AWS stacks (AWS API Gateway and below) are managed via the serverless configurations of each service. 
Usually there is a PROD and TEST stage deployment, and sometimes a DEV deployment too.


## Cloud configuration

These components are configured so that the stack functions correctly. Asd they're rarely touched they are maintained manually,
 via the AWS Consolce unless stated otherwise.

 - Elastic Search API is an AWS Kibana/Elastic managed service. Objects stored in ToshiAPI are indexed here, and used via the Weka Search UI.

 - SSL certificates are issued via AWS Certificate Manager (ACM) for the Domain hosts used by NSHM (see us-east-1 region).

 - AWS Cloudfront provides a global content delivery service and maps SSL domain host onto the internal services names via cloudfront host names.

 - GNS Internal IT manage the DNS zone entriesfor NSHM SSL certificates, hostnames, and verifcations.

 - Google Analytics (not configured)

Lower levels of the AWS stack (AWS API Gateway and below) are generally managed via the serverless configurations of each service.

## Stack diagram

```mermaid
graph TD
    classDef nshm stroke:lightgreen, stroke-width:3px
    classDef nshm-deprecated stroke:red, stroke-width:1px

    classDef AWS stroke:orange, stroke-width:3px
    classDef SVC stroke:powderblue, stroke-width:3px
    classDef note stroke:black, stroke-width:1px
    
    W["Weka web app
        weka.gns.cri.nz"]:::nshm
    NB3["{API_HOST}
        /weka-app-api/graphql"]:::note 

    subgraph GW["Weka Application Gateway layer"]

        SSL["SSL: {API_HOST}"]:::AWS
        
    CF["DNS: {API_HOST} CNAME {Cloudfont HOST}"]:::AWS

        CF -.-|/weka-app-api| C

        C["AWS API Gateway:
        nshm-weka-apigw"]:::AWS
        
        F2["nshm-weka-apigw"]:::nshm

        C -->|path: /weka-app-api/graphql| F2

    end

    SSL --- CF

    W -.-|graphql query| NB3 -.-> SSL

    subgraph SUP["graphql microservices layer"]
        direction TB

        ES_API[elastic-search-api]:::AWS
        S-API[nshm-model-graphql-api]:::nshm
        T-API[nshm-toshi-api]:::nshm
        M-API[nshm-model-api]:::nshm

    end

    subgraph DEP["unused microservices"]
        direction TB

        H-API[nshm-hazard-api]:::nshm-deprecated
        Q-API[nshm-search-api]:::nshm-deprecated
    end

    F2 -.-> SUP
    SUP ---> DEP

```
