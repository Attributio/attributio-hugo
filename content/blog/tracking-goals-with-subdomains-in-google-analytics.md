+++
title = "Tracking Goals with Subdomains in Google Analytics"
date = "2017-05-18"
lastmod = "2019-07-16"
tags = ["google analytics"]
categories = ["tutorial"]
banner = "/img/blog/201705/subdomain_page_filter.png"
keywords = "google analytics, google analytics subdomain tracking, google analytics goals with subdomains"
description = "Track goals for your subdomains with the same universal tracking code from Google Analytics."
author = "Attributio"
aliases = [
    "/blog/2017/05/18/tracking-goals-with-subdomains-in-google-analytics/"
]
+++


## Introduction

Sometimes your conversion funnel spans multiple domains or subdomains. If you need to track destination url goals on a subdomain for an existing universal analytics property, you can follow the steps below to distinguish between root domain visitors and subdomain visitors along with goals that might have the same url path. This is not to be confused with cross-domain tracking which requires different configuration settings.

## Step 1 - Set cookie domain to auto

Add the universal analytics tracking code from your root domain to your subdomain and ensure that the cookie domain is set to auto (by default it is set in universal analytics unless you are using GTM).
 
## Step 2 - Add a referral exclusion list

Add your subdomain to the referral exclusion list. That way, Google doesn't set the referrer as your subdomain when your visitors jump between your root domain and subdomain, when it should be set to the originating source like an ad or search.

<br>

<img class="img-responsive img-thumbnail" src="/img/blog/201705/add_referral_exclusion.png" alt="gogole analytics referral exclusion for subdomain" />

<br>


## Step 3 - Add a filter to your GA view

Add a subdomain filter to your view. Since the most common goals are destination goals and Google Analytics utilizes the Request URI (path) as the match value, we need to distinguish between subdomain paths and root domain paths. Google by default only matches against the path information so we need to modify the path data to include the subdomain in our filter.

You want to select the advanced filter and extract the hostname (your subdomain) and concatenate it with the request uri (your path), and store it as the new path. In the example below we only do this for subdomains. You could do this for every path [shown here](https://support.google.com/analytics/answer/1012243?hl=en) .


<br>

<img class="img-responsive img-thumbnail" src="/img/blog/201705/subdomain_page_filter.png" alt="view filter for hostname path google analytics sub domain" />

<br>


## Step 4 - Set goals

Set up your goals with the destination path if you have the default requrest uri set, or with the hostname included if your filter is set up that way. See the examples below for a path only set up for the root domain and a hostname and path set up for the subdomain. 

Notice that they share the same path and Google Analytics would have counted them as the same goal if we did not explicitly make that distinction in our filtered view.

<div class="row">
<div class="col-md-6">
<h4>Root Domain Goal</h4>
<img class="img-responsive img-thumbnail" src="/img/blog/201705/root_domain_goal.png" alt="root domain goal for google analytics" />
</div>

<div class="col-md-6">
<h4>Subdomain Goal</h4>
<img class="img-responsive img-thumbnail" src="/img/blog/201705/subdomain_goal.png" alt="subdomain goal for google analytics" />
</div>
</div>

## Step 5 - Set autolinker (for cross domain only)

If you have a different domain but want to track it under the same property, you need to configure Google Analytics to allow linker like so:

```javascript
  ga('create', 'UA-XXXXXXX-Y', 'auto', {'allowLinker': true});
  ga('require', 'linker');
  ga('linker:autoLink', ['example-2.com']);
```

In Google Tag Manager you will need to set the Field Name of Fields to Set add "allowLinker" as the Field Name and set the Value to "true". Under Cross Domain Tracking, add a comma separated list of domains that you want to share the client id under the Auto Link Domains field.

## Conclusion

There you have it. Now you're ready to start tracking across multiple subdomains. If you need help tracking your goals across multiple domains or subdomains to collect analytics for your leads [request a consultation today!](/meet/)