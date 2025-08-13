NSHM public web applications require a Cloudfront distribition to:

 1. provide the HTTPS transport for the website see also [Manage SSL Certificates](./manage_ssl_certifates.md)
 1. reduce load time for the end users. (but see Cache Invalidation below)

This approach is used in Weka, Kororaa and for a couple of supplementary web sites too.


## Apply HTTPS to an S3 static website

 - decide the DNS name for the distribution
   e.g `nshm-static-reports-test.gns.cri.nz`
 - in Certificate Manager 
   - request an SSL certificate
   - pass details to GNS IT support for verification

- To be continued ....
