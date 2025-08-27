NSHM web applications are deployed using the **AWS S3 _Static web site_** feature.

This approach is used in Weka, Kororaa and for a couple of supplementary web sites.
 
## S3 bucket setup

 1. Create an S3 bucket named for the project e.g. `nzshm22-weka-ui-prod`. 
   You can use an existing NSHM website bucket as a template, but some additional config is still needed.
 1. Build the static web content. This may be automated using `yarn build` or similar, and 
   likely requires some configuration via environment variables or secrets. 
 1. Copy the static web content into the bucket, with the main index.html in the root of the bucket.
   This can be automated using github actions e.g. [weka deploy_test_to_s3.yml](https://github.com/GNS-Science/weka/blob/main/.github/workflows/deploy_test_to_s3.yml).
 1. There are some configuraton settings still needed on the S3 bucket. See [this tutorial](https://docs.aws.amazon.com/AmazonS3/latest/userguide/HostingWebsiteOnS3Setup.html) for details 
   and look at an existing NSHM website to use as a template. 

The S3 bucket should be publically accessible via its' Website endpoint. This is a hostname in the **amazon.com** domain and does not support HTTPS. These limitations mean we mostly want to create a Custom DNS config for the web site.

Note that this setup process is done just once for each website (we typically have both TEST and PROD endpoints). But the build, test, deploy steps are done 
often, and these are automated in **Github Actions** as shown above.

## Custom hostname configuration

In this example we will configure a new public hostname for our website **weka.gns.cri.nz**. We will need an SSL certificate, some DNS configuration, and an **AWS CloudFront
distribution** to tie everything together.

 - **DNS names**. We have already chosen a name for this website (**weka.gns.cri.nz**) but if you need a new one you'll want to define that now.
 - An **SSL Certificate** is required for Secure HTTP (HTTPS). For this we use the **AWS Certificates** manager which integrates readily, and is easy to use. 
   See this page for a guide and email templates to use with IT support (who manage DNS for the **gns.cri.nz** domain).
 - Now we can configure the **AWS CloudFront distribution** see [this page for details](./setup_a_cloudfront_distribution.md).

Once these step are completed, you should have functional and secure website running at **https://weka.gns.cri.nz**. Congrats.
