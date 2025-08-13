# A checklist for deploying the Weka stack to production

This page captures at a high-level all the steps required to deploy the weka application and all its component parts.
Some of these steps are only ever done once, while many will be repeated as new features or updates are applied.

The new reader can familiarise themself with the [NSHM Web stacks](/nzshm-documentation/architecture/api_gateway_deployments/) for an overview of how the APIs share 
some common configuration. 

Please see [Weka stack](/nzshm-documentation/architecture/weka_deployment_stack/) for details of the current Weka stack. It is made up of graphql microservices, consolidated into an appliciation gatewy, to which the Weka web app connects.

## Deployment Strategy

It's pretty straightforward... we must work up from the bottom to the top, since almost everything depends on something at a lower level.
We expect that each service component should have enough testing and QA in place so that the service contract with its clients is well defined and documented. 

We want to be sure that in our deployment environment:

- each microservice API is operating and has the correct release version.
- the application gateway has a current schema for each microservice and is proxying the correct microservice endpoints.
- that public API URI (DNS names/paths) map to the correct API gateway service.
- the Web Application is served from its public URI e.g **weka.gns.cri.nz**.
- the Web Application is connecting to the API correctly e.g **nshm-api.gns.cri.nz/weka-app-api/graphql**.

It is very rarely that we need to configure and check all of these at once. More commonly, a new User feature requires both API and UI changes.
Typically this would require change in a particular microservice (and possibly it's underlying library), a schema refresh for the APIGW, and then some UI changes in the web application.  

Some elements of the stack are setup up once and are very unlikely to need change. These include:

 - DNS names for the public facing application and API endpoints
 - SSL Certificates for these are valdiated once, and then set to auto refresh.
 - Mapping the public facing API URIs to the correct API gateway service.
 - CloudFront caching for the web application. (although cache invalidation may be needed on each app deployment)

See [deploy a web app](./deploy_a_web_app.md) for details on completing these steps.

