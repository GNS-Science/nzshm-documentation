## React UI Project Guidelines

### Testing, Coverage and Linting

We typically use Jest for unit tests and Cypress for end to end testing.
For linting we use eslint with the plugins react/recommended, @typescript-eslint/recommended, prettier/recommended.
We use Husky to run linting on commit and unit tests on push, our Cypress specs run on merge to deploy-test or main.

### Integration & Deployment

For each site we usually have two deployed branches:

 - **MAIN** is the live, public facing product. 

 - **DEPLOY-TEST** is used for verifying new features prior to public release.

These are continuously deployed to from their respective branches using github actions.
In UI projects, the folder `.github/workflows` typically contains:

 - a `browser-tests.yml` which runs our end to end specs on deployment to either main or deploy-test.
 - a `deploy-test-to-s3.yml` which builds, configures and deploys the deploy-test branch.
 - a `deploy-prod-to-s3.yml` which builds, configures and deploys the main branch.
