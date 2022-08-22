+++
title = "How to Unblock Google Analytics"
date = "2018-06-25"
lastmod = "2019-08-19"
tags = ["google analytics"]
categories = ["tutorial"]
banner = "/img/blog/201806/ublock.png"
keywords = "unblock google, google analytics conversion tracking, google analytics attribution, custom attribution model with google analytics, remove direct google analytics, wordpress google analytics, wordpress adblock google analytics"
description = "A simple way to unblock adblockers that may be skewing your analytics data."
author = "Attributio"
aliases = [
    "/blog/2018/06/25/how-to-unblock-google-analytics-in-wordpress/",
    "/how-to-unblock-google-analytics-in-wordpress/",
]
+++


## Adblockers

Adblocking is on the rise. And with it comes not only the removal of ads but the blocking of popular web traffic tracking tools like Google Analytics. 

Some reports suggest that more than 10% of all web traffic is now being blocked from services like Google Analytics and this can be a major issue for businesses that rely on accurate data to make good business decisions.

## Specific Problems

You might find that the conversions being reported in Google Analytics don't actually reflect the conversions that you are seeing in the backend of your website. 

This could be for a variety of reasons, one of which is that Google Analytics is being blocked by those particular users that are using adblocking software.

## A simple solution

By hosting the Universal Analytics Script on your server and creating a proxy to send hit data to Google Analytics, the [Attribution Unblock Analytics plugin](https://wordpress.org/plugins/attributio-unblock-analytics/) will ensure that when Google Analytics is being blocked, a backup script will load and fire the standard scripts and any custom hit data you add to the plugin.

<br>

<img class="img-responsive img-thumbnail" src="/img/blog/201806/attributio-plugin.png" alt="unblock google analytics plugin for wordpress" />

<br>

As seen in the example below, a common extension used to block Google Analytics is detected and triggers the self hosted Analytics script and sends hit data along with any custom scripts added to the backend to the proxy created by the plugin and routes it back to Google.

<br>

<img class="img-responsive img-thumbnail" src="/img/blog/201806/analytics-unblock.png" alt="unblock adblockers google analytics" />

<br>

## Analytics tracking alternatives

Due to the popularity of Google Analytics, there are quite a few resources to block popular platforms like Google and Facebook. And rather than trying to unblock Google, you can roll out your own Analytics.

By storing sessions on your visitor's browser and stroing them in your database, CRM, or externally hosted form builder, you can collect source, medium, campaign, and even keyword data.

As a free tool Google Analytics is great. But it takes time to familiarize yourself with all of the bells and whistles and takes an expert to configure proper tracking.

By creating custom scripts to suit your needs, you don't need to unblock google analytics, you can start tracking sesssions on your own and collect the data you need to grow your business.