NSHM public web resources use Cloudfront distributions to:

 1. **Support HTTP/S** (secure) transport for the website.
 1. **Cache content** to reduce load time for the end users. (but see Cache Invalidation below)

This approach is used for Weka and Kororaa web apps, the API gateways, and for a couple of supplementary static web sites too,
 basically any web content where we want SSL / HTTP/S tranport encryption. The caching is a nice bonus but does require
 a little extra management for our SPA web apps.

## Configure HTTP/S for an AWS web service

### Process steps 

- Decide the DNS host name for the distribution. This should be something identifiable in the organisation domain e.g. `nshm-static-reports-test.gns.cri.nz`.

- Create a new **AWS CloudFront** distribution for the S3 bucket. Inititally, without an SSL certificate, which will be added later.
  Now we just want to note down the new **Cloudfront DNS name** (e.g `1234ABCD.cloudfront.com`).

- In **AWS Certificate Manager** 
    1. create a new SSL certificate for the DNS host name, selecting DNS validation. Mostly just defaults can be selected here.
    1. take note of the DNS entry that needs to be configured for validation.
- Raise a ticket with IT support, requesting new **DNS configuration** for:
    1. the SSL certificate CNAME record - for DNS verification.
    1. the Cloudfront CNAME record - so `nshm-static-reports-test.gns.cri.nz` will return the host address defined 
   by the Cloudfront DNS name.
- When the **DNS configuration** is completed:
    1. Check that the Certicate is showing as valid in **AWS Certificate Manager** 
    1. In **AWS CloudFront**, assign the SSL certificate to the distribution.

- **Testing**
    1. Check that the two host names (GNS and CloudFront ) both resolve to the same IP address.
    1. Check that the GNS domain now supports the HTTPS protocol.

If the tests complete OK, then then we're done. 

## Cache Invalidation

This is typically relevant to the **Kororaa** and **Weka** Single Page Apps (SPA). Immeidiately after each new deployment it it advisable to invalidate the assocatied distribution (using `/*`). This helps to keep all the subcomponebts of the application 'in sync'. Without this sometimes rather odd errors can occur because of mixed components= versions.

By contrast:

 - API requests are not cached, so never require invalidation
 - Static sites are very unlikely to see existing urls with content changes - so unlesss this happens, invalidation is not needed.
 