+++
title = "How to Unblock Google Analytics in Wordpress"
date = "2018-06-25"
tags = ["google analytics"]
categories = ["tutorial"]
banner = "/img/blog/201806/ublock.png"
keywords = "google analytics conversion tracking, google analytics attribution, custom attribution model with google analytics, remove direct google analytics, wordpress google analytics, wordpress adblock google analytics"
description = "A simple way to unblock adblockers that may be skewing your analytics data."
author = "Attributio"
+++


## Adblockers
Adblocking is on the rise. And with it comes not only the removal of ads but the blocking of popular web traffic tracking tools like Google Analytics. Some reports suggest that more than 10% of all web traffic is now being blocked from services like Google Analytics and this can be a major issue for businesses that rely on accurate data to make good business decisions.

## Specific Problems
You might find that conversions that are being reported in Google Analytics don't actually reflect the conversions that you are seeing in the backend of your website. This could be for a variety of reasons, one of which is that Google Analytics is being blocked by those particular users that are using adblocking software.

## A simple solution
By hosting the Universal Analytics Script on your server and creating a proxy to send hit data to Google Analytics, the [Attribution Unblock Analytics plugin](https://wordpress.org/plugins/attributio-unblock-analytics/) will ensure that when Google Analytics is being blocked, a backup script will load and fire the standard scripts and any custom hit data you add to the plugin.

<br>

<img class="img-responsive img-thumbnail" src="/img/blog/201806/attributio-plugin.png" alt="unblock google analytics plugin for wordpress" />

<br>

As seen in the example below, a common extension used to block Google Analytics is detected and triggers the self hosted Analytics script and sends hit data along with any custom scripts added to the backend to the proxy created by the plugin and routes it back to Google.

<br>

<img class="img-responsive img-thumbnail" src="/img/blog/201806/analytics-unblock.png" alt="unblock adblockers google analytics" />

<br>

If you need help unblocking your google analytics on your website, we have experts standing by to [configure your analytics for optimal tracking. Meet Your Expert Today!](/join/)

We also recommend our clients to utilize additional tools like <a href="https://shareasale.com/r.cfm?b=462846&u=1517931&m=46217&urllink=&afftrack=">Improvely</a>. They have a great feature that profiles your customers so you can have a granular look at how they arrived, how much they spent, and what their behavior was on your site.

