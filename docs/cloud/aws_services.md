 NSHM project uses **Amazon Web Services (AWS)** for a our **24/7 services** (e.g. Public web sites, APIs and datatsets), and also for **compute tasks** like modelling. 
 
We employ a serverless architecture to ensure that fixed operating costs are minimised.

Here're the key services we use, with some context:
 
### AWS S3 (SimpleStorageService)

This the preferred storage service for NSHM, for it's cost/performance and flexibility. It's used for:
 
  - NSHM dataset storage (notably the NSHM Hazard datasets were migrated here from DynamoDB),
  - large object storage for the [ToshiAPI service](../components/nshm_toshi_api.md),
  - general object storage for graphql API services,
  - Serverless deployments for graphql API services,
  - CI/CD deployments for the Public Websites,
  - Static website deployments e.g. [nzshm22-static-reports](http://nzshm22-static-reports.s3-website-ap-southeast-2.amazonaws.com/opensha/index.html)

We have an [NSHM_Storage Dashboard (ap-southeast-2)](https://ap-southeast-2.console.aws.amazon.com/s3/lens/dashboard/NSHM_Storage_Dash?region=ap-southeast-2) configured in 
the **AWS Console**.

We have experimented with Other Bucket types, but to date we use only ***General Purpose*** buckets and primarily the **Standard** storage class.

### Amazon OpenSearch Service (formerly ElasticSearch)

This search engine is used to index the contents of Toshi API, and supports the Search Feature of the [Weka Application](../components/weka.md). 

This service is the main outlier in our primarily serverless project, using a pay-per-minute model for a 24/7 service. Here  We run a single PROD instance, and a couple of test/dev instances, using the smallest possbile instance configuration to keep costs down.

See AWS [OpenSearch Domains (ap-southeast-2)](https://ap-southeast-2.console.aws.amazon.com/aos/home?region=ap-southeast-2#opensearch/domains)

### DynamoDB

This is a big-table style **NoSQL** database service with a serverless pay-for-usage model. We use it where necessary to provide performant queries on well structured data, but we are migrating more static data away where possible to keep costs down and improve science community access 
e.g for our [**Hazard Data Migration project**](https://github.com/GNS-Science/toshi-hazard-store/issues/72).

The main usage in NSHM is for the metadata storage layer of the [ToshiAPI service](../components/nshm_toshi_api.md), where four tables contain > 15 million objects.

See AWS [DynamoDB Dashboard (ap-southeast-2)](https://ap-southeast-2.console.aws.amazon.com/dynamodbv2/home?region=ap-southeast-2#dashboard)

### Lambda

All NSHM web APIs are [**serverless**](../cloud/serverless_framework.md), meaning that their compute is handled by Lambda functions, without "always on" web server infrastructure. In [NSHM Web Stacks](../architecture/api_gateway_deployments.md) there's a diagram showing how these are configured.

NSHM lambda functions use Python3, excpet for the Graphql API Gateways which use Node. This is because graphql stitching
features needed in the API Gateway services are only available from the [Apollo Graphql](https://www.apollographql.com/docs) who use the Node ecosystsem with javascript/typescript.

  - [Lambda discover (ap-southeast-2)](https://ap-southeast-2.console.aws.amazon.com/lambda/home?region=ap-southeast-2#/discover) lists all the lambdas.
  - [Lambda Applications (ap-southeast-2)](https://ap-southeast-2.console.aws.amazon.com/lambda/home?region=ap-southeast-2#/applications) lists the lambda deployment stacks.

## API Gateway
cloud/aws_api_gateway.md

## CloudFormation
cloud/aws_cloudformation.md

## CloudFront
cloud/aws_cloudfront.md

## Certificate Manager

Amazon Certificates Manager is used to produce SSL certificates. It produces auto-renewing certificates that are easily
integrated with the wider AWS ecosystem e.g Cloudfront. 

See [Setup a Cloudfront Distribution](../guidelines/setup_a_cloudfront_distribution.md) 

See AWS [Certificates Manager](https://us-east-1.console.aws.amazon.com/acm/home?region=us-east-1)

## IAM
cloud/aws_iam.md

## Backup
cloud/aws_backup.md      

## Batch
cloud/aws_batch.md      

## EC2
cloud/aws_ecs2.md    
