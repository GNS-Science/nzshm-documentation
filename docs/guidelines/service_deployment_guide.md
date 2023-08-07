## API service deployment pattern

### Deployment environment standards

For a typical service, two API service environments are available:

 - **PROD** (short for production) is the live, public facing product. 
   In deployment repositories,  the `main` (occasionally `master`) commit branch represents the currently live state.

 - **TEST** is used for verifying new features prior to publice release.
   In deployment repositories,  the `deploy-test` commit branch represents the currently live state.

Occasionally an additional **DEV** (for development) service environment may be deployed. These are usually discarded as soon as possible to minimise cost and clutter.

### Automated deployments

Most NSHM projects make use of [Github Actions](https://docs.github.com/en/actions) to run automated QA and deployments. This helps us provide ensure stable and reproduceable processes across all the API services. 

API service projects all use the [serverless framework](https://serverless.com) to manage complexities and boilerplate steps required to maintain the underlying service architecture. This framework supports a range of cloud service envionments. The NSHM project is currently using just AWS cloud services.

In API projects, the folder `.github/worflows` typically contains:

 - a `run-tests.yml` workflow which defines the QA steps - testing, linting, etc.

 - a `dev.yml` workflow that runs QA whenever a PR is opened/updated on `deploy-test` or `main` branches.

 - `deploy-to-aws.yml` workflow that runs both QA and deployment steps when a PR is merged to `deploy-test` or `main` branches.

for example, see these workflow files for  [solvis-graphql-api](https://github.com/GNS-Science/solvis-graphql-api/tree/main/.github/workflows)

