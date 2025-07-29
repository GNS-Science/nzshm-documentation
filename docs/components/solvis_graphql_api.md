## Solvis graphql API

[![Build Status](https://github.com/GNS-Science/solvis-graphql-api/actions/workflows/dev.yml/badge.svg)](https://github.com/GNS-Science/solvis-graphql-api/actions/workflows/dev.yml)
[![codecov](https://codecov.io/gh/GNS-Science/solvis-graphql-api/branch/main/graphs/badge.svg)](https://codecov.io/github/GNS-Science/solvis-graphql-api)

A graphql API wrapping the [solvis library](./solvis.md) for analysis of opensha modular Inversion Solutions.

Provides analytical services to help explore and analyse key components of the NSHM source rate model.

## Links

 - [Github: GNS-Science/solvis-graphql-api](https://github.com/GNS-Science/solvis-graphql-api)
 - [Dependent projects](https://github.com/GNS-Science/solvis-graphql-api/network/dependents)


## Deployments

Note that the both TEST and PROD share the same GITHUB environmemt because `serverless.yml` handles any stage specifics internally. Notably the solvis-store table names.

-----
### PROD
-----

| AWS lambda function name                                    | Github Environment | Branch       |
| ----------------------------------------------------------- | ------------------ | ------------ | 
| nzshm22-solvis-graphql-api-prod-app                         |                | main  | 
| nzshm22-solvis-graphql-api-prod-warmup-plugin-littleWarmer  |                | main  | 


-----
### TEST
-----

| AWS lambda function name                                    | Github Environment | Branch       |
| ----------------------------------------------------------- | ------------------ | ------------ | 
| nzshm22-solvis-graphql-api-test-app                         |                | deploy-test  | 
| nzshm22-solvis-graphql-api-test-warmup-plugin-littleWarmer  |                | deploy-test  | 


## Cache table preparation 

For any new models, or for a new environment the required Solvis Store tables must first be populated. This is done using the `cli` script found in the `solvis-store` project.

**Tables:** 
 
 - `SOLVIS_RuptureSetParentFaultRuptures-{PROD|TEST}`

 - `SOLVIS_RuptureSetParentFaultRuptures-{PROD|TEST}`

**ENV setup:**
```
export DEPLOYMENT_STAGE=PROD
export REGION=ap-southeast-2
export AWS_PROFILE=toshi_batch_devops
```

### Parent fault cache

```
solvis-store$ poetry run cli parents ../solvis-graphql-api/solvis_graphql_api/composite_solution/NSHM_v1.0.4_CompositeSolution.zip
solvis-store tasks - populate store.
fault system key: CRU
model: SOLVIS_RuptureSetParentFaultRuptures-PROD<RmlsZToxMDAwODc=, Acton>, Acton, 0, 2
2023-07-31 17:01:28 INFO     botocore.credentials Found credentials in shared credentials file: ~/.aws/credentials
model: SOLVIS_RuptureSetParentFaultRuptures-PROD<RmlsZToxMDAwODc=, Aka Aka>, Aka Aka, 1, 2
model: SOLVIS_RuptureSetParentFaultRuptures-PROD<RmlsZToxMDAwODc=, Akatarawa>, Akatarawa, 2, 41
...
```

### Location Radius cache

```
solvis-store$ poetry run cli radius  ../solvis-graphql-api/solvis_graphql_api/composite_solution/NSHM_v1.0.4_CompositeSolution.zip
solvis-store tasks - populate store.
fault system key: PUY
model: SOLVIS_RuptureSetLocationDistances-PROD<RmlsZToxMjkwOTg0, IVC:200>, radius: 200, ruptures: 1119
2023-07-31 17:15:05 INFO     botocore.credentials Found credentials in shared credentials file: ~/.aws/credentials
model: SOLVIS_RuptureSetLocationDistances-PROD<RmlsZToxMjkwOTg0, MON:200>, radius: 200, ruptures: 172
...
```


### Smoke-test query

```
query {
  about 
  filter_ruptures(filter: {
    model_id:"NSHM_v1.0.4"
    fault_system:"CRU"
    corupture_fault_names:["BooBoo", "Chamberlain", "Akatarawa"]
    radius_km:10
    location_ids:["WLG"]
  })
   {
        total_count
    edges {
      node {
        rate_weighted_mean
        rupture_index
        magnitude
        area
      }
    }
  }
}
```

returns:

```
{
  "data": {
    "about": "Hello World, I am solvis_graphql_api! Version: 0.8.4",
    "filter_ruptures": {
      "total_count": 25,
      "edges": [
        {
          "node": {
            "rate_weighted_mean": 0.0000017483932879258646,
            "rupture_index": 282028,
            "magnitude": 7.738,
            "area": 3454
          }
        },
        {
          "node": {
            "rate_weighted_mean": 0.00000343733654517564,
            "rupture_index": 282710,
            "magnitude": 7.769,
            "area": 3704
          }
        },
        {
          "node": {
            "rate_weighted_mean": 3.43733006502589e-7,
            "rupture_index": 282712,
            "magnitude": 7.775,
            "area": 3760
          }
        },
        {
          "node": {
            "rate_weighted_mean": 5.651207857226836e-7,
            "rupture_index": 283970,
            "magnitude": 7.824,
            "area": 4203
          }
        },
        {
          "node": {
            "rate_weighted_mean": 4.951539622766177e-8,
            "rupture_index": 284644,
            "magnitude": 7.849,
            "area": 4453
          }
        }
      ]
    }
  }
}
```

