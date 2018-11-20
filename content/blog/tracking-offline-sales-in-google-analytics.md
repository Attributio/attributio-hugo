+++
title = "Tracking Offline Sales in Google Analytics"
date = "2018-11-19"
tags = ["google analytics", "crm", "offline sales"]
categories = ["tutorial", "google analytics"]
banner = "/img/blog/201811/revenue.png"
keywords = "google analytics, google analytics offline sales, track offline sales"
description = "Track all of your offline sales figures in Google Analytics so you can measure your ROI."
author = "Attributio"
+++


## Configure your lead generation forms to store Google's cookies

If you're collecting leads online and converting them over the phone through your CRM, you need to collect a cookie that Google Analytics sets on your website to identify that user. Once you store that unique id in your CRM, you can send a webhook to Google Analytics with that id via their <a href="https://developers.google.com/analytics/devguides/collection/protocol/v1/parameters">Measurement Protocol</a> whenever a deal has been completed. 

## Configure Google Analytics to store revenue data

You will also need to create a custom metric in your Google Analytics property to represent revenue data (you can do this easily with our <a href="https://app.attribut.io?utm_medium=blog">app</a>). Once that has been set, you can send the client id that was captured during the online lead conversion process along with the total value of that deal to Google Anaytics to get a picture of your ROI.

If you can't collect the client id, which Google uses to match all of that user's behavior in Google Analytics with the data that you want to see, you will need to send a User ID. If you aren't using an authentication system where your customers have id's associated with their accounts, you can just add the id generated from your CRM and send that along with the revenue data. You will need one or the other, otherwise Google Analytics will not register the event data that you will be sending to it's servers.

Lastly, you will need to create a calculated metric that will divide the revenue with the cost.

## Create a report in Google Analytics to show attribution data with revenue and ROA

In Google Analytics you will need to create a report that lists the custom metric you created with revenue and the calculated metric along with the cost of advertising.

<br>

<img class="img-responsive img-thumbnail" src="/img/blog/201811/revenue.png" alt="gogole analytics track offline sales" />

<br>

And there you have it. Now you can track the ROI of all your advertising in Google Analytics along with all of your sales that happen offline.

Next, we'll take a look at how to add cost data related to our advertising to Google Analytics.
