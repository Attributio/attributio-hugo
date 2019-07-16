+++
title = "The Ultimate Guide to Measure ROI On Your Direct Marketing Efforts With Salesforce & Google Analytics - Part 1"
date = "2018-11-21"
tags = ["google analytics", "crm", "offline sales", "salesforce", "ROA"]
categories = ["tutorial", "google analytics"]
banner = "/img/blog/201811/lead-form-1.png"
keywords = "google analytics, google analytics offline sales, track offline sales, salesforce, measure roa, measure roi, salesforce roi, marketing roi"
description = "Part 1 of a step by step guide to setting up your Salesforce account to measure ROI on ads, campaigns, and keywords in Google Analytics ."
author = "Attributio"
aliases = [
    "/blog/2018/11/21/the-ultimate-guide-to-measure-roi-on-your-direct-marketing-efforts-with-salesforce-and-google-analytics-1/"
]
+++


## Brand Marketing VS Direct Marketing

> You can't manage what you can't measure.

> *- Peter Drucker*

We live in an age when we can measure just about everything. The fact that many of us aren't measuring our direct marketing efforts is detrimental to our businesses. 

Brand marketing continues to be difficult to measure since brand marketing is more about communicating values to an audience. The ROI on that kind of advertising is measured far down the line whereas direct marketing is about getting conversions and selling right off the bat.

## Measuring Your Marketing

Companies of the past used to throw millions into their advertising budget without ever getting any kind of accurate indication of how those efforts rolled over into sales.

Today, those companies are fading and a new generation of companies are springing up with the tools to measure their direct marketing efforts to maximize their profits.

With a set of tools and a bit of configuration, you can be well on your way to measuring the ROI on your direct marketing efforts to compete with the new generation of guirella marketers taking down old encumbents.

## Using Salesforce & Google Analytics To Measure Your Results

You don't have to use a CRM. You can use your POS, your ecommerce shop, or your ERP system. Anything you use to store transaction data. In our example, we'll use Salesforce since it's the most common CRM and Google Analytics since it's the most widely available analytics tool.

You'll need to first follow <a href="https://support.google.com/analytics/answer/7584446?hl=en" target="_blank">these instructions</a> to configure your Leads and Opportunites to be able to store data that is provided by Google Analytics. For detailed instructions, continue reading.

### Create Lead & Opportunity Fields In Salesforce

1. Navigate to the Object Manager Tab and select the "Lead" object
2. Select "Fields & Relationships"
3. Select "New"
4. Select "Text" in the radio options and then select "Next"
5. Fill in the form as follows:
	* Field Label = GA Client ID
	* Length = 255
	* Field Name = GACLIENTID


	<img class="img-responsive img-thumbnail" src="/img/blog/201811/lead-gclid.png" alt="salesforce gclid leads" />

6. Leave all the default fields in the subsequent pages and save
7. Repeat with Leads, Accounts, and Opportunities with these three fields:
	* GACLIENTID
	* GAUSERID
	* GATRACKID
	* GAREVENUEID

8. "Set History Tracking" for all new fields

	<img class="img-responsive img-thumbnail" src="/img/blog/201811/lead-history.png" alt="salesforce gclid set lead history" />

9. "Map Lead Fields" between Lead, Account, and Opportunity fields

	<img class="img-responsive img-thumbnail" src="/img/blog/201811/lead-map.png" alt="salesforce gclid map leads" />

### Create Custom Dimensions & Metrics In Google Analytics

This part is easy. We created a <a href="https://app.attribut.io" target="_blank">simple tool</a> to help you create these fields in your Google Analytics Property.

You'll also want to send the Client ID & User ID back to Google Analytics as a custom dimension if you want to run some more complex analyses of your campaigns. You can find instructions <a href="https://attribut.io/blog/2017/04/27/track-conversions-with-google-analytics-client-id/">here</a>.

### Create a Web-To-Lead Form

1. In Salesforce navigate to Platform Tools > Feature Settings > Marketing > Web-to-Lead and create a new form.

	<img class="img-responsive img-thumbnail" src="/img/blog/201811/lead-form-1.png" alt="salesforce gclid lead form start" />

2. Add the fields you want for your form making sure to add the fields we created earlier.

	<img class="img-responsive img-thumbnail" src="/img/blog/201811/lead-form-2.png" alt="salesforce gclid lead form setup" />

3. Add the rendered html form to our website and make the tracking fields hidden.
4. Grab the Client ID from Google Analytics along with User ID (If you have it) and auto-populate the hidden fields. If you're using Google Tag Manager, you're code will differ than what is presented below. You need to make the Client ID available as a cookie and grab the cookie and populate the hidden field. As for the Tracking ID, you can either manually add it to the form as a value or dynamically populate it.

	<img class="img-responsive img-thumbnail" src="/img/blog/201811/lead-form-html.png" alt="salesforce gclid lead form setup" />


## Next Steps

Now that you have Salesforce and Google Analytics setup, you'll need to <a href="/blog/2018/12/05/the-ultimate-guide-to-measure-roi-on-your-direct-marketing-efforts-with-salesforce-and-google-analytics-2/">configure Salesforce to send deal values to Google Analytics</a>. To get help, <a href="/join/">consult with a marketing attribution expert today</a>.

We also recommend our clients to utilize additional tools like <a href="https://shareasale.com/r.cfm?b=462846&u=1517931&m=46217&urllink=&afftrack=">Improvely</a>. They have a great feature that profiles your customers so you can have a granular look at how they arrived, how much they spent, and what their behavior was on your site.

