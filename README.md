# Hosting static web content in AWS

This repo contains a very simple CloudFormation template that will help you stand up a static website at a domain name for which you have a public hosted zone in Route53:

You need:
* A public hosted zone in Route53, e.g. example.com
* Some content.  You can use the assets/index.html file in this repo to get started

The rest of the machinery gets created for you, namely:
* A non-public (i.e. accessible only within your account, the default) S3 bucket
* A CloudFront distribution in front of that bucket
* An AWS Certificate manager certificate for the domain name for this site, so that it can be served over HTTPS
* The template automates DNS validation of your certificate
* DNS records in Route53 for IPv4 and IPv6

To get started:
1. Launch the template at cfn/main.yaml.  You will need to specify the domain name at which you want to run this site, e.g. mysite.example.com; and the Route53 id of the public hosted zone for example.com.  Because a CloudFront distribution takes a while to deploy (15-30m), this step will take some time.
2. Copy some content into the S3 bucket created by the template.  You will need at least an index.html.  Don't forget the `ContentType: text/html`
