# NSHM Hazard processing flow
```mermaid
flowchart TD
    classDef nshm stroke:lightgreen, stroke-width:3px
    classDef AWS stroke:orange, stroke-width:3px
    classDef SVC stroke:powderblue, stroke-width:3px   
    
    subgraph NSHM Hazard
        direction TB

        subgraph P1[Stage 1]
            direction TB

            RHR[/run hazard realizations/]:::nshm
            runzi:::nshm
            oq[openquake]
            HR[(hazard realizations)]:::AWS

            RHR --> |with| runzi
            runzi -->|using| oq 
            runzi -->|produces| HR
        end

        subgraph P2[Stage 2]
            direction TB

            RHA[/run hazard aggregations/]:::nshm
            thp[toshi-hazard-post]:::nshm
            HA[(hazard aggregations)]:::AWS

            RHA -->|with| thp
            thp -->|produces| HA            
        end

        subgraph P3[Stage 3]
            direction TB

            RHD[/run hazard disaggregations/]:::nshm
            thp2[toshi-hazard-post]:::nshm
            HD[(hazard disaggregations)]:::AWS

            RHD -->|with| thp2
            thp2 -->|produces| HD            
        end

    end
    ENV{any of}
    AWS[NSHM AWS Batch]:::AWS
    HPC[HPC Cluster]:::SVC
    LOCAL[Local Workstation]

    %% links
    P1 -.-> |using| ENV
    P2 -.-> |using| ENV
    P3 -.-> |using| ENV

    ENV --> AWS
    ENV --> HPC
    ENV --> LOCAL
    

```

## NSHM AWS services for Hazard

```
mermaid
graph TD
    classDef nshm stroke:lightgreen, stroke-width:3px
    classDef AWS stroke:orange, stroke-width:3px
    classDef SVC stroke:powderblue, stroke-width:3px
        
    batch[[Batch]]:::AWS
    EC2:::AWS    
    Fargate:::AWS    

    dynamoDB[(DynamoDB)]:::AWS
    s3[("Simple Storage S3")]:::AWS
    ENV{any of}
    batch --> ENV
    batch --> Fargate

```

```
mermaid
graph LR
    classDef nshm stroke:lightgreen, stroke-width:3px
    classDef AWS stroke:orange, stroke-width:3px
    classDef SVC stroke:powderblue, stroke-width:3px

    subgraph AWSENV[NSHM AWS environment]
        ths[toshi-hazard-store]:::nshm
        thp[toshi-hazard-post]:::nshm
        
        tapi[toshi-api]:::nshm

        oq[openquake]
        thp -.->ths
        thp -.-> AWS
        thp -.-> tapi
        R -.-> tapi
        
        %% R -.-> thp
        R-.->|runs| thp -.->|on| AWS
        R-.->|runs| oq -.->|on| AWS
        
        ths -.-> AWS

    end  
```