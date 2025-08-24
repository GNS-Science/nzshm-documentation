The NSHM project uses the **Serverless Framework** from [serverless.com](https://www.serverless.com) to standardise and simplify devops for AWS service deployment.

Each NSHM API has a `serverless.yml` file which describes the API deployment. Serverless is deployed locally using NPM, and provides developer commands that, with the appropriate access permissions, can deploy, manage, and interact with the application stack from a developer machine. These same commands in github CI/CD scripts to automate deployment into the TEST and PROD environments.

## serverless.yml

The [Serverless.yml Reference](https://www.serverless.com/framework/docs/providers/aws/guide/serverless.yml) is the canonical guide. We use the serverless.yml to:

 - define the application name, and components.
 - control the stages and regions where deployments occur.
 - define any additional AWS resources and permissions.
 - configure serverless plugins (such as lamabda `warming` functions).

## Serverless CLI

Here, the [CLI reference](https://www.serverless.com/framework/docs/providers/aws/cli-reference) is canonical. We commonly ese these commands for
local devops:

 - [`sls deploy`](https://www.serverless.com/framework/docs/providers/aws/cli-reference/deploy) 
 - [`sls info`](https://www.serverless.com/framework/docs/providers/aws/cli-reference/info) 
 - [`sls logs`](https://www.serverless.com/framework/docs/providers/aws/cli-reference/logs) 
 - [`sls remove`](https://www.serverless.com/framework/docs/providers/aws/cli-reference/remove) 
 - [`sls login`](https://www.serverless.com/framework/docs/providers/aws/cli-reference/login) is needed with framework V4.
    See [alternatives discussion](#future--alternatives) below 

## Future / Alternatives

When NSHM services were originally developed (2020-2022) serverless framework was non commercial. That has now changed, requiring 
users to register services using the V4 API. Users must also declare whether these are eligible for free
or paid usage. This change is effective from V4, and will soon be required for all projects, because of version 
support limits on the old API.

One of the key 'advantages' for the serverless.conm framework is support for cloud providers other than AWS. However, for NSHM the 
effort involved in such a migration might be too large to consider in the foreseable future.

Alternative options:

  - [AWS SAM](https://aws.amazon.com/serverless/sam/) is an AWS alternative - supporting [Cloudformation (CF)](), but also [Terraform (??)](https://aws.amazon.com/blogs/compute/better-together-aws-sam-cli-and-hashicorp-terraform/).
  - [AWS CDK](https://aws.amazon.com/cdk/) is anothedr AWS offering - wrapping CF with various language APIs (eg Python, Go, Javascript)
  - [Hashicorp Terraform](https://developer.hashicorp.com/terraform/intro) - which does not use CF, has different service offerings, and cloud provider options.

