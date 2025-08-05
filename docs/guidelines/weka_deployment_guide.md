# A checklist for deploying the Weka stack to production

This page captures at a high-level all the steps required to deploy the weka application and all its component parts.
Some of these steps are only ever done once, while many will be repeated as new features or updates are applied.

## Background info

The reader can familiarise themsel with the following material...

 - The microservice architecture (link)
     - [NSHM web service API overview](/nzshm-documentation/architecture/services/)
     - [NSHM Web stacks](/nzshm-documentation/architecture/api_gateway_deployments/)

## Weka stack components 

- see [Weka stack](/nzshm-documentation/architecture/weka_deployment_stack/)

## Deployment Strategy

It's pretty straightforwad. We must work up from the bottom to the top, because almost everything depends on something at a lower level e.g. `kororaa -> kororaa-graphql-apigw -> solvis-graphql-api -> solvis`. In turn, solvis needs `pandas, numpy, geopandas, pyproj, shapely` etc.

Some basic assumptions:

 - that each component should have enough testing and QA in place so that the service contract with it's clients is well defined and testable. 
 - component unit tests use mock/stubbing to replace any dependent service / API calls.

## Then 

 - AWS Cloud Formation configuration. (link)
 - NSHM DNS config and SSL certificates. (link) 

 - [ ] identifying all the stack components

## Testing the component parts

## Testing the integration

* integration steps (graphql schema APIGW updates)

* one-off configuration and testing steps (via AWS tools and IT support dependencies)

Domain names

SSL certificates

API Gateway config

CloudFront distributions