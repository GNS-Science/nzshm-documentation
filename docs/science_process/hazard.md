# Hazard processing flows

```mermaid
flowchart TD
    classDef nshm stroke:lightgreen, stroke-width:3px
    classDef AWS stroke:orange, stroke-width:3px
    classDef SVC stroke:powderblue, stroke-width:3px   
    
    subgraph P1[Hazard processing]
        RHR[/run hazard realizations/]:::nshm
        RHA[/run hazard aggregations/]:::nshm
        RHD[/run hazard disaggregations/]:::nshm
    end

    ENV{any of}
    AWS[NSHM AWS Batch]:::AWS
    HPC[HPC Cluster]:::SVC
    LOCAL[Local Workstation]

    %% links
    P1 -.-> |using| ENV
    ENV --> AWS
    ENV --> HPC
    ENV --> LOCAL      
```
TODO: describe the boxes

## Hazard Realizations

```mermaid
flowchart LR
    classDef nshm stroke:lightgreen, stroke-width:3px
    classDef AWS stroke:orange, stroke-width:3px

    RHR[/run hazard realizations/]:::nshm
    runzi:::nshm
    oq[openquake]
    HR[(hazard realizations)]:::AWS

    RHR --> |with| runzi -->|using| oq -->|produces| HR 
```
TODO: describe the boxes

## Hazard Aggregrations

```mermaid
flowchart LR
    classDef nshm stroke:lightgreen, stroke-width:3px
    classDef AWS stroke:orange, stroke-width:3px

    RHA[/run hazard aggregations/]:::nshm
    thp[toshi-hazard-post]:::nshm
    HA[(hazard aggregations)]:::AWS

    RHA -->|with| thp -->|produces| HA            
```
TODO: describe the boxes

## Hazard Disaggregrations

```mermaid
flowchart LR
    classDef nshm stroke:lightgreen, stroke-width:3px
    classDef AWS stroke:orange, stroke-width:3px

    RHD[/run hazard disaggregations/]:::nshm
    thp[toshi-hazard-post]:::nshm
    HD[(hazard disaggregations)]:::AWS

    RHD -->|with| thp -->|produces| HD            
```
TODO: describe the boxes

## NSHM Hazard infrastructure WIP

TODO ... 

```mermaid
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

```mermaid
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
        thp -.-> tapi -.-> AWS

        
        %% R -.-> thp
        thp -.->|on| AWS
        
        ths -.-> AWS

    end  
```