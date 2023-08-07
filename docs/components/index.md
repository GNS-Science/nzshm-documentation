this is a list of all the NSHM project components managed by Computational Working Group (CWG).

## Web service  API gateways

 - [Kororaa Application API Gateway](nshm_kororaa_apigw.md) a stitched graphql API for Kororaa.
  

## microservice APIs

 - [Solvis Graphql API](solvis_graphql_api.md) a graphql API for analysis of opensha modular Inversion Solutions.

 - [Kororaa Graphql API]() app specific features.     
   NB this currently includes hazard, which should have a domain microservice.

 - [Toshi API]() Toshi API. nshm-toshi-api

## All NSHM API and Gateway endpoints

### PROD (LIVE)

| repo: GNS-Science/ | local_folder | lambda | endpoint | APIGW | Desc |
| -------------- | ------------ | ------ | -------- | ------| ---- |
| kororaa-graphql-api | kororaa-graphql-api | nzshm22-kororaa-api-prod-app | https://29zzl5pqb0.execute-api.ap-southeast-2.amazonaws.com/prod/graphql | prod-nzshm22-kororaa-api | kororaa-functions |


### PROD (INCOMING)

| repo: GNS-Science/ | local_folder | lambda | endpoint | APIGW | Desc |
| -------------- | ------------ | ------ | -------- | ------| ---- |
| nshm-kororaa-apigw | nshm-kororaa-apigw | nshm-kororaa-apigw-prod-app |  https://8wq8w9xika.execute-api.ap-southeast-2.amazonaws.com/prod/graphql | prod-nshm-kororaa-apigw |gateway |
| kororaa-graphql-api | kororaa-graphql-api | nzshm22-kororaa-api-prod-app | https://29zzl5pqb0.execute-api.ap-southeast-2.amazonaws.com/prod/graphql | prod-nzshm22-kororaa-api | kororaa-functions |
| solvis-graphql-api | solvis-graphql-api | nzshm22-solvis-graphql-api-prod-app | https://42ncm9rc71.execute-api.ap-southeast-2.amazonaws.com/prod/graphql | prod-nzshm22-solvis-graphql-api | solvis functions |
| nshm-toshi-api | nshm-toshi-api | nzshm22-toshi-api-prod-app |  https://aihssdkef5.execute-api.ap-southeast-2.amazonaws.com/prod/graphql|  prod-nzshm22-toshi-api | toshi API |


### TEST (LIVE)
| repo: GNS-Science/ | local_folder | lambda | endpoint | APIGW | Desc |
| -------------- | ------------ | ------ | -------- | ------| ---- |
| nshm-kororaa-apigw | nshm-kororaa-apigw | nshm-kororaa-apigw-test-app | https://4ra58fifn3.execute-api.ap-southeast-2.amazonaws.com/test/graphql |  test-nshm-kororaa-apigw | gateway |
| kororaa-graphql-api | kororaa-graphql-api | nzshm22-kororaa-api-test-app |  https://kh7np169je.execute-api.ap-southeast-2.amazonaws.com/test/graphql |  test-nzshm22-kororaa-api | kororaa-functions |
| solvis-graphql-api | solvis-graphql-api | nzshm22-solvis-graphql-api-test-app |  https://ciied31tx2.execute-api.ap-southeast-2.amazonaws.com/test/graphql | test-nzshm22-solvis-graphql-api | solvis functions |
| nshm-toshi-api | nshm-toshi-api | nzshm22-toshi-api-test-app | https://i7gz6msaa2.execute-api.ap-southeast-2.amazonaws.com/test/graphql |  test-nzshm22-toshi-api | toshi API |
