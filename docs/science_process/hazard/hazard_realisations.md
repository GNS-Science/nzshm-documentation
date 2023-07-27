## Produce Hazard realisations

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

NSHM SRM LT has 49 parts (ref NSHM)

For each leaf of the source rate model logic tree:

**Run a job with**

### inputs:
 - inversion solution and distributed seismicity rate models (multiple) for the fault systems. i.e. one part of the Source LT)
 - gmms
 - GMM Logic Tree
 - site specifications config
 - user configs IMTS, etc
 - calculation configs

### outputs:
  - one HDF5 file, size (TBA): NZSHM22 4k sites => 300 MB
  - CSV files: 200MB
  - optional export to DynamoDB =>  THH Hazard Realizations table
  - optional export to cache table => THH Hazard Realizations CACHE
  
### resource/cost/metrics:
 
 - 49 * 300MB of realisations for NSHM model => 15GB
 - Currently ~24 hours for 4k sites, all NSHM periods. AWS M5 instance 8 CPU.

