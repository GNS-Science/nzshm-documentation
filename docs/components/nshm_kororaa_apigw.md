# Kororaa Application API Gateway

A stitched graphql API for Kororaa, which amalgamates the function-specific apis into an application API Gateway for the NSHM web app (aka Kororaa).

- [on github](https://github.com/GNS-Science/nshm-kororaa-api)

For more info, please see the [Api Gateway Pattern](/nzshm-documentation/architecture/api_gateway_pattern/) page.

## Deployments

Deployment environments AWS_TEST and AWS_PROD each define the following variables:

```
NZSHM22_KORORAA_API_KEY
NZSHM22_KORORAA_API_URL
NZSHM22_SOLVIS_API_KEY
NZSHM22_SOLVIS_API_URL
NZSHM22_TOSHI_API_KEY
NZSHM22_TOSHI_API_URL
```

### lambda function

-----
### TEST
-----

| AWS lambda function name                                    | Github Environment | Branch       |
| ----------------------------------------------------------- | ------------------ | ------------ | 
| nzshm22-XXX-test-app                         |                | deploy-test  | 
| nzshm22-XXX-test-warmup-plugin-littleWarmer  |                | deploy-test  | 


### API gateway configuration
| AWS  (API gateway)                     | Github Environment | Branch       |
| -------------------------------------- | ------------------ | ------------ | 
| test-nshm-kororaa-apigw (4ra58fifn3)   | AWS_TEST           | deploy-test  | 
