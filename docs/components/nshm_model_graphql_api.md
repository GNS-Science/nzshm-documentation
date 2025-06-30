

## NSHM Model Graphql API

A graphql API graphql API wrapping the nzshm-model library. 

**Github:** [GNS-Science/nshm-model-graphql-api](https://github.com/GNS-Science/nshm-model-graphql-api)

## Deployments

Note that the both TEST and PROD share the same GITHUB environmemt because `serverless.yml` handles any stage specifics internally. 

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

