+++
title = "The Ultimate Guide to Measure ROI On Your Direct Marketing Efforts With Salesforce & Google Analytics - Part 2"
date = "2018-12-05"
tags = ["google analytics", "crm", "offline sales", "salesforce", "ROA"]
categories = ["tutorial", "google analytics"]
banner = "/img/blog/201812/sf-process-builder.png"
keywords = "google analytics, google analytics offline sales, track offline sales, salesforce, measure roa, measure roi, salesforce roi, marketing roi"
description = "Part 2 of a step by step guide to setting up your Salesforce account to measure ROI on ads, campaigns, and keywords in Google Analytics ."
author = "Attributio"
aliases = [
    "/blog/2018/12/05/the-ultimate-guide-to-measure-roi-on-your-direct-marketing-efforts-with-salesforce-and-google-analytics-2/"
]
draft = true
+++

## Send Revenue Data To Google Analytics

In the <a href="/blog/2018/11/21/the-ultimate-guide-to-measure-roi-on-your-direct-marketing-efforts-with-salesforce-and-google-analytics-1/">Part 1 of Measuring Roi With Salesforce and Google Analytics</a>, we provided a step by step guide on configuring Google Analytics and setting up a Web-to-lead form with Salesforce and getting all of that configured on your website. In this post, we're going to set Salesforce up to send revenue data to Google Analytics

### Configure remote site settings in Salesforce

1. Navigate to Setup > Settings > Security > Remote Site Settings and create a new setting
	<img class="img-responsive img-thumbnail" src="/img/blog/201812/sf-new-remote-site.png" alt="salesforce send revenue to google analytics" />
2. Create new setting as seen below:
	<img class="img-responsive img-thumbnail" src="/img/blog/201812/sf-new-remote-site-create.png" alt="salesforce send revenue to google analytics" />

### Create Apex Class in Salesforce

We're going to need to create an Apex class to handle our get requests to Google Analytics via the Measurement Protocol. Keep in mind that the client id is a required field and revenue data sent without this field will not be registered in Google Analytics.

Go to Setup > Developer Console > File > New > Apex Class and create a new class with an invocable method with invocable variables that sends a get request to Google Analytics with the varialbes that we will map from our Opportunity.

Now navigate to Setup > Platform Tools > Process Automation > Process Builder and create a new process. You can create an action that will be triggered when an Opportunity is Won and map the fields of that opportunity to the Apex Class that we just created as shown below:

<img class="img-responsive img-thumbnail" src="/img/blog/201812/sf-process-builder.png" alt="salesforce opportunity won send google analytics" />

And that's it. Now you can send revenue data to Google Analytics every time your sales agents close a deal and you can do a detailed cost analysis based on your advertising campaigns and even identify the most profitable keywords to really take your marketing efforts to the next level.

If you would like to download a package for Salesforce, <a href="/meet/">reach out to us</a> and we will send you a link to install the package and that you can demo along with documentation to complete the configuration process.

We also recommend our clients to utilize additional tools like <a href="https://shareasale.com/r.cfm?b=462846&u=1517931&m=46217&urllink=&afftrack=">Improvely</a>. They have a great feature that profiles your customers so you can have a granular look at how they arrived, how much they spent, and what their behavior was on your site.