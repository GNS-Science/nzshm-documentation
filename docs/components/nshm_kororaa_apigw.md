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
| nshm-kororaa-apigw-test-app                          |                | deploy-test  | 
| nshm-kororaa-apigw-test-warmup-plugin-littleWarmer  |                | deploy-test  | 


### API gateway configuration
| AWS  (API gateway)                     | Github Environment | Branch       |
| -------------------------------------- | ------------------ | ------------ | 
| test-nshm-kororaa-apigw (4ra58fifn3)   | AWS_TEST           | deploy-test  | 


```
Deploying nshm-kororaa-apigw to stage test (ap-southeast-2)
WarmUp: Creating warmer "littleWarmer" to warm up 1 function

✔ Service deployed to stack nshm-kororaa-apigw-test (79s)

api keys:
  KORORAA_APIGW_TempApiKey-test: G4C***nx - Api key until we have an auth function
endpoints:
  OPTIONS - https://4ra58fifn3.execute-api.ap-southeast-2.amazonaws.com/test/{any+}
  POST - https://4ra58fifn3.execute-api.ap-southeast-2.amazonaws.com/test/{any+}
  GET - https://4ra58fifn3.execute-api.ap-southeast-2.amazonaws.com/test/{any+}
functions:
  app: nshm-kororaa-apigw-test-app (11 MB)
  warmUpPluginLittleWarmer: nshm-kororaa-apigw-test-warmup-plugin-littleWarmer (1.2 kB)
Serverless Domain Manager:
  Domain Name: nshm-api-test.gns.cri.nz
  Target Domain: d1g45pget0a502.cloudfront.net
  Hosted Zone Id: Z2FDTNDATAQYW2

```

#### DNS and SSL manual configuration

There are a few manual steps to complete because DNS hosting for GNS is handled in-house. The public facing api URL `nshm-api-test.gns.cri.nz` is run by the AWS API Gateway service layer. This requires an SSL certificate, which must be validated by GNS DNS. The setup steps are:

  - use **AWS Console/Certificate Manager** to create an SSL certificate request e.g. for `nshm-api-test.gns.cri.nz`. 
  
  - pass the CNAME details to IT support and ask them to setup the SSL CNAME validation entry.

  - run `sls create_domain --stage test` which will configure the new API gateway mapping for the lambda

  - using **AWS Console/API Gateway/Custom domain names** to get the cloudfront address that the gateway is mapped to (e.g. `d1g45pget0a502.cloudfront.net`). Ask IT support to add a new CNAME entry mapping the GNS DNS name to `.cloudfront.net`.

Note these manual steps are needed only once for each domain host. Additonal mappings may now be added freely.