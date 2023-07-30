
The NSHM Computational Working Group (CWG) documentation project covers:

```mermaid
graph TD
    SP[Scientific Processes]
    SA[Systems Architecture]
    TG[Technical Guidelines]
    TI[Technology Index]
    SP -.- SA
    SP -.- TG
    %%TI -.- SA
    %% SA -.- TI -.- TG
    %%SA -.- TG
```

 - **NSHM CWG [Scientific Process](./science_process/)** describes the processes and tools used to run experiments and build the NSHM models.

 - **NSHM CWG [Systems Architecture](./architecture/)** covers the overarching design of the tools, services used run, publish and support the NSHM.

 - **NSHM CWG Technical Guidelines** describes standards and common technical processes used by the CWG team to maintain and operate the NSHM systems. 

 - **NSHM CWG Index** is a list of all the NSHM project components.

## Project-wide documentation
_where more detail can be found_ 

 - Science publications etc

## Diagram Legend

We use the following convention throughout the diagrams 

```mermaid
graph TD
    classDef nshm stroke:lightgreen, stroke-width:3px
    classDef AWS stroke:orange, stroke-width:3px
    classDef SVC stroke:powderblue, stroke-width:3px

    a1[AWS service]:::AWS
    a2[Cloud service]:::SVC
    l2[NSHM code]:::nshm
    l3[external code]
```
## NSHM vs NZSHM

These two acronyms are used quite interchangelbly throughout the project. Either can be found widely e.g. in repository names, Science publications, etc, etc

 - **NSHM** stands for National Seismic Hazard Model
 - **NZSHM** stands for New Zealand Seismic Hazard Model

```mermaid
graph LR
    NZSHM -->|is a| NSHM 
```
**NZSHM _is a_ NSHM** . There there are others e.g. the Canadian NSHM, the Japan NSHM). We use NZSHM to specifically identify the **NSHM of Aotearoa New Zealand**. While **NZHSM22** refers to the NZSHM version first published in 2022.

```mermaid
graph LR
    NZSHM22 -->|is a version of the| NZSHM
```

## Documentation maintenance

Please see the [README](./readme.md) file.