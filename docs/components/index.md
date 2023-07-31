this is a list of all the NSHM project components managed by Computational Working Group (CWG).

## Web service APIs

 - [Kororaa Application API Gateway](nshm_kororaa_apigw.md) a stitched graphql API for Kororaa.
  
 - [Solvis Graphql API](solvis_graphql_api.md) a graphql API for analysis of opensha modular Inversion Solutions


## Sanity API gateway endpoints

### PROD (LIVE)

| repo: GNS-Science/ | local_folder | lambda | endpoint | APIGW | Desc |
| -------------- | ------------ | ------ | -------- | ------| ---- |
| kororaa-graphql-api | kororaa-graphql-api | nzshm22-kororaa-api-prod-app | https://29zzl5pqb0.execute-api.ap-southeast-2.amazonaws.com/prod/graphql | prod-nzshm22-kororaa-api | kororaa-functions |
| nshm-toshi-api | nshm-toshi-api | nzshm22-toshi-api-prod-app |  https://aihssdkef5.execute-api.ap-southeast-2.amazonaws.com/prod/graphql|  prod-nzshm22-toshi-api | toshi API |
| solvis-api| solvis-api | nzshm22-solvis-api-prod-app |  https://mmbzw56f1h.execute-api.ap-southeast-2.amazonaws.com/prod/{proxy+} | prod-nzshm22-solvis-api | REST API |

### PROD (INCOMING))

| repo: GNS-Science/ | local_folder | lambda | endpoint | APIGW | Desc |
| -------------- | ------------ | ------ | -------- | ------| ---- |
| nshm-kororaa-api | nshm-kororaa-api | | | |gateway |
| kororaa-graphql-api | kororaa-graphql-api | nzshm22-kororaa-api-prod-app | https://29zzl5pqb0.execute-api.ap-southeast-2.amazonaws.com/prod/graphql | prod-nzshm22-kororaa-api | kororaa-functions |
| solvis-graphql-api | solvis-graphql-api | nzshm22-solvis-graphql-api-prod-app | https://42ncm9rc71.execute-api.ap-southeast-2.amazonaws.com/prod | prod-nzshm22-solvis-graphql-api | solvis functions |
| nshm-toshi-api | nshm-toshi-api | nzshm22-toshi-api-prod-app |  https://aihssdkef5.execute-api.ap-southeast-2.amazonaws.com/prod/graphql|  prod-nzshm22-toshi-api | toshi API |


### TEST
| repo: GNS-Science/ | local_folder | lambda | endpoint | APIGW | Desc |
| -------------- | ------------ | ------ | -------- | ------| ---- |
| nshm-kororaa-api | nshm-kororaa-api | 	nshm-kororaa-apigw-test-app | https://4ra58fifn3.execute-api.ap-southeast-2.amazonaws.com/test/{any+} |  test-nshm-kororaa-apigw | gateway |
| kororaa-graphql-api | kororaa-graphql-api | nzshm22-kororaa-api-test-app |  https://kh7np169je.execute-api.ap-southeast-2.amazonaws.com/test/graphql |  test-nzshm22-kororaa-api | kororaa-functions |
| solvis-graphql-api | solvis-graphql-api | nzshm22-solvis-graphql-api-test-app |  https://ciied31tx2.execute-api.ap-southeast-2.amazonaws.com/test/{any+} | test-nzshm22-solvis-graphql-api | solvis functions |
| nshm-toshi-api | nshm-toshi-api | nzshm22-toshi-api-test-app | https://i7gz6msaa2.execute-api.ap-southeast-2.amazonaws.com/test/graphql |  test-nzshm22-toshi-api | toshi API |
