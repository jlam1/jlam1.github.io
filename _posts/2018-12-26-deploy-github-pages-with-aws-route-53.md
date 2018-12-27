---
layout: post
title: How to deploy github pages with AWS Route 53 and using ACM to certify domain
tags: [aws, route 53, acm, github pages]
---

This is a small guide from registering a domain name with AWS, specifically Route 53, get it certified via ACM and creating a github page for a static generating site. 
The idea was to create a portfolio and personal blog page for my projects. I will go over the steps in creating this site.

You will need to have registered for both [GitHub](https://github.com/) and [AWS](https://aws.amazon.com/) accounts beforehand.

## Registering a domain name via Route 53
1. Go to [https://console.aws.amazon.com](https://console.aws.amazon.com)
2. Search for service name `Route 53`
3. Choose a domain name and check for availability, cost is roughly ~$12/year
4. Once purchased on the sidebar click on `hosted zones` and select your domain
5. Create a record, set no value to name, set type to `A - IPv4 address`, set `Alias` to `NO` and input these four ip addresses into the `Value`
~~~
185.199.108.153 
185.199.111.153 
185.199.109.153 
185.199.110.153
~~~
![R53-1](https://johnjlam.com/img/posts/2018-12-26/r53-1.PNG)
6. Create a another record, set value to `www`, set type to `A - IPv4 address`, set `Alias` to `YES` and the alias target should be your domain name
![R53-1](https://johnjlam.com/img/posts/2018-12-26/r53-2.PNG)

## Certify domain name using ACM
1. Go to [https://console.aws.amazon.com](https://console.aws.amazon.com)
2. Search for service name `ACM` or `Certificate Manager`
3. Click `Request a certificate`
![ACM-1](https://johnjlam.com/img/posts/2018-12-26/acm-1.PNG)
4. Request a public certificate
![ACM-2](https://johnjlam.com/img/posts/2018-12-26/acm-2.PNG)
5. Add your domain name that you have registered with Route 53, make sure to add an `*.` in front of your domain name. e.g. `*.johnjlam.com`
![ACM-3](https://johnjlam.com/img/posts/2018-12-26/acm-3.PNG)
6. Validation method should be `DNS validation` to make validation of your certification request much quicker (this is not the case if the domain was registered elsewhere)
![ACM-4](https://johnjlam.com/img/posts/2018-12-26/acm-4.PNG)
7. Click the arrow down for more options then click the option to `Create a record in Route 53`
8. Official documentation can be found here [https://docs.aws.amazon.com/acm/latest/userguide/gs-acm-validate-dns.html](https://docs.aws.amazon.com/acm/latest/userguide/gs-acm-validate-dns.html)

## Creating the repo for github page
Either create an empty respository in the format of username.github.io or fork over a jekyll theme which I opt for.
The theme I am currently using came from [Beautiful Jekyll](https://github.com/daattali/beautiful-jekyll#readme) by daattali. 
Make any changes under the file name `_config.yml` which includes alot of options in terms of sitename, google analytics, or changing navigation headers. More details is under his readme file.
1. Rename repo to `username.github.io`
2. Go into Settings
3. Under `GitHub Pages` section, select the source to `master branch` and save
4. The custom domain name goes here, e.g. `johnjlam.com`
5. Enable `Enforce HTTPS`
![GHP-1](https://johnjlam.com/img/posts/2018-12-26/ghp-1.PNG)

## Test
Visit your website by entering your domain name without `https://` or `www`, you should be redirected to `https://custom-domain-name.com`.

## Sources
* [GitHub Pages](https://pages.github.com/)
* [Jekyll](https://jekyllrb.com/)
* [Beautiful Jekyll](https://github.com/daattali/beautiful-jekyll#readme)
* [Amazon Web Services](https://aws.amazon.com/)
* [AWS Route 53](https://aws.amazon.com/route53/)
* [AWS Certification Manager](https://aws.amazon.com/certificate-manager/)