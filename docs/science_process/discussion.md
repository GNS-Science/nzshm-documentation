
# CBC / CDC notes on CWG goals for 2024 NSHM phase

GOALS: 

 - Make NSHM processes more easily reproducible for 3rd parties
 - Make NSHM processes more efficient => less compute time to reach useful outputs

NB 2nd goal supports the former, as one impediment to reproducability is the cost of setting up/running NSHM variants.

---- 
## Model review tools..

NSHM primary tools for analysis of Rupture Sets, Grand Inversions and Hazard are wrapped up in TUI, with some Kororaa features to be backwards ported.

 - Q: Can we make these tools useful to 3rd parties? 

### 3rd party tools
 - Opensha reporting on Rupture sets or Inversions (The Solution Files [TSF]), and also hazard.
 - scecVdo 3D analysis on opensha solution files.

### NSHM tools

 - TUI wraps uses opensha reporting, providing flip-chart like report view comparisons.

 - solvis library provide analysis tool for TSF for python developers.

 - Kororaa and TUI web apps provide rupture maps tools based on solvis.

 - toshi-API (id and storage)

  Q: can we make the 'big services' optional for 3rd parties?

----
## Building new Inversions and Rupture Sets 

### Making Opensha more configurable...

i.e. Let users tweak the configs. 

So that users can override standard parts of NSHM with variations - e.g. additional paleo data. e.g

 - build new rupture sets: modify faults, modify connectivity
 - run new inversions: modify constraints, weights, etc

- Q: What is possible without Java development (for 3rd parties)? 

- Q: how to compare with NZSHM 22

 -Q: can we make NSHM hazard model comparisons easy

----

## Building custom hazard models

The following four sections each now has a page, but the questions are captured below.

### Hazard processing flows

### [NSHM Hazard realisations](/nzshm-documentation/science_process/hazard/hazard_realisations/)

 - Q: for 3rd party, how many OQ jobs are needed? from 1-100.

 - Q: can anyone do it off-cloud? Yes it's just time.

 - Q: can CUDA be used here?

 - Q: what optimisations are possible (GEM)

 - Q: what else can be compared to openquake for this calcluation. opensha, [NSHMP](https://www.usgs.gov/software/nshmp-lib), bespoke? 


### [Hazard Aggregrations](/nzshm-documentation/science_process/hazard/hazard_aggregations/)

 - Q: how to make it more resilient to AWS errors
 
 - Q: can we do it without DynamoDB/AWS
 
### [Disagg Realisations](/nzshm-documentation/science_process/hazard/disagg_realisations/)

 - Q: can we store this in DB? 

 - Q: how big will it become (multiply hazard realizations by 1000 for 7 PoEs)
 
 - Q: would optimisations to Hazard also benefit here?? Maybe not so much as the single site.

**Notion for possible improvement**

If, when calcluating hazard curves, the disaggs could be stored as a byproduct. Some calculation , but main cost would is storage and extra I/O.

  - hazard cals would need more granular IMTL grid. 

  - more IMTLS = more storage

### [Disagg Aggregations](/nzshm-documentation/science_process/hazard/disagg_aggregations/)

 - Q: how to make it more resilient to AWS errors

 - Q: can we do it without DynamoDB/AWS