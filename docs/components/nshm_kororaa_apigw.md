# Kororaa Application API Gateway

A stitched graphql API for Kororaa, which amalgamates the function-specific apis into an application API Gateway for the NSHM web app (aka Kororaa).

- [on github](https://github.com/GNS-Science/nshm-kororaa-api)

## Deployments

### lambda function

| AWS lambda function name                                    | Github Environment | Branch       |
| ----------------------------------------------------------- | ------------------ | ------------ | 
| nzshm22-solvis-graphql-api-test-app                         | TEST               | deploy-test  | 
| nzshm22-solvis-graphql-api-test-warmup-plugin-littleWarmer  | TEST               | deploy-test  | 

### API gateway
| AWS  (API gateway)                     | Github Environment | Branch       |
| -------------------------------------- | ------------------ | ------------ | 
| test-nshm-kororaa-apigw (4ra58fifn3)   | AWS_TEST           | deploy-test  | 
