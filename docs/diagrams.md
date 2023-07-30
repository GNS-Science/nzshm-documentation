# About mermaid Diagrams

These docs use the mermaid javascript library to render diagrams automatically using a simple syntx (similar to that used plantUML). 

Diagrams can be built easily in a text exidor and many editiros will automatically preview these for you live.

## ALERT: issue with mermaid v10 SYNTAX

FYI there's a open issue https://github.com/squidfunk/mkdocs-material/issues/5758 to be aware of. It's actively being worked on.

Some newer (v10) mermaid syntax features are not yet supported by mkdocs.

The v9.4 syntax for mermaid is applicable now (see https://github.com/mermaid-js/mermaid/blob/release/9.4.3/docs/syntax/flowchart.md).


NB I'm wanting some multi-line text, and markdown formatting but it seems these a v10 only :(

```mermaid
graph LR

    A["Client A
    multiline works"]

    B["`**Client B**
    markdown is not rendered (in mkdocs)`"]
    
    C[Load Balancer]
    A ---> C
    B --> C
```


# Test Mermaid

```mermaid
graph TD
A[Client] --> B[Load Balancer]
B --> C[Server01]
B --> D[Server02]
E[Extra blob] -.- D
```

## Snippets


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