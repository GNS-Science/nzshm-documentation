## API devops training

This document contains a small set of exercises to help familiarise one with the devops tooling annd processes for NSHM web app  stacks (Kororaa and Weka).

## Quiz 1 (pre)

 - what is a graphql web API.
 - what is another common web API technology known as? (clue:acronym)
 - what is the interactive graphql web UI called?
 - and how does one normally access it?
 - is the graphql API documtation searchable?
 - what is a stitched graphql API?
 - name any non-graphql web APIs used in the NSHM application stack?


## Exercise 1 - Use a graphql API service locally.

Pick one of:

 - solvis-graphql-api
 - nshm-model-graphql-api
 - kororaa-graphql-api

Then:

 - check it out locally.
 - follow the readme/docs to install & test.
 - run the service locally.
 - test the service locally via the igraphql web UI.

Finally, demonstrate to the team:

 - accessing the web UI locally with a web browser.
 - using a `query`  provided by the API to retrieve something
    relevant to the NSHM project. (e.g. a map, a rupture, a standardised location).
 
## Exercise 1A - manually deploy a serverless service

## Caution:
 The permissions required for this AWS action are such that the user could inadvertently deploy the stack 
 to an incorrect location (region/stage). We want to avoid any risk of collision with thee 'real' services 
 running in ap-southeast-2 prod/test. Some work on region boundaries is warranted to mitigate this concern.

 For this exercise we will use `region=us-east-1 stage=dev`

 ## Goal
 Deploy your service (from Exercise 1) to the AWS cloud and validate it.

 _Note use of  `region=us-east-1 stage=dev` for all the following:_

 - First. check the service does not exist already:

    `npx serverless info --region us-east-1 --stage=dev`

- deploy the service:

    `npx serverless deploy --region us-east-1 --stage=dev`

Once sucessfully deployed note the endpoint and token details, and use your
browser to reproduce the results from Exercise 1 above.

## Potential issues: 

 - `poetry export` fails as it's been removed from latest version
    
    fix `poetry self add poetry-plugin-export` 

 - AWS credential not sufficient to deploy.

   fix: Ask for these permissions in AWS account.

- `Resource handler returned message: "Unzipped size must be smaller than 262144000 bytes ....`
 
  As python packages versions change sometimes this limit may be exceeded,

  Various techniques for addressing this, ask for help.


## Exercise 2 - Use the weka graphql API gateway service.

**Instructions:**

 - check it out locally https://github.com/GNS-Science/nshm-kororaa-apigw
 - follow the readme / docs
 - run the service locally, using remote PROD schemas.
 - test the service locally using the igraphql web UI.
**Demo**

Finally, demonstrate to the team:

 - accessing the web UI locally with a web browser.
 - using a `query`  provided by the API to retrieve something
    relevant to the NSHM project. (e.g. a map, a rupture, a standardised location).
 
## Exercise 3 - Use the weka graphql API gateway service locally.


