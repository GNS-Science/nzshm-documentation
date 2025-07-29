

## NSHM Model Graphql API

A graphql API wrapping the [nzshm-model](/nzshm-documentation/components/nzshm_model/) library. 

[![Build Status](https://github.com/GNS-Science/nshm-model-graphql-api/actions/workflows/dev.yml/badge.svg)](https://github.com/GNS-Science/nshm-model-graphql-api/actions/workflows/dev.yml)
[![codecov](https://codecov.io/gh/GNS-Science/nshm-model-graphql-api/branch/main/graphs/badge.svg)](https://codecov.io/github/GNS-Science/nshm-model-graphql-api)

## Links

 - [Github: GNS-Science/nshm-model-graphql-api](https://github.com/GNS-Science/nshm-model-graphql-api)
 - [Dependent projects](https://github.com/GNS-Science/nshm-model-graphql-api/network/dependents)


## Deployments

Note that the both TEST and PROD share the same GITHUB environment because `serverless.yml` handles any stage specifics internally. 

-----
### PROD
-----

| AWS lambda function name                                    | Github Environment | Branch       |
| ----------------------------------------------------------- | ------------------ | ------------ | 
| nzshm22-model-graphql-api-prod-app                         |                | main  | 
| nzshm22-model-graphql-api-prod-warmup-plugin-littleWarmer  |                | main  | 


-----
### TEST
-----

| AWS lambda function name                                    | Github Environment | Branch       |
| ----------------------------------------------------------- | ------------------ | ------------ | 
| nzshm22-model-graphql-api-test-app                         |                | deploy-test  | 
| nzshm22-model-graphql-api-test-warmup-plugin-littleWarmer  |                | deploy-test  | 


**ENV setup:**
```
export DEPLOYMENT_STAGE=PROD
export REGION=ap-southeast-2
export AWS_PROFILE=toshi_batch_devops
```

### Smoke-test query

```
query {
  about
  version 
}
```

