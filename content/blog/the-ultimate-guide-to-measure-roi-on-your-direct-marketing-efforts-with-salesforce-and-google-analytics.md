+++
title = "The Ultimate Guide to Measure ROI On Your Direct Marketing Efforts With Salesforce & Google Analytics"
date = "2018-11-21"
tags = ["google analytics", "crm", "offline sales", "salesforce", "ROA"]
categories = ["tutorial", "google analytics"]
banner = "/img/blog/201811/lead-form-1.png"
keywords = "google analytics, google analytics offline sales, track offline sales, salesforce, measure roa, measure roi, salesforce roi, marketing roi"
description = "Part 1 of a step by step guide to setting up your Salesforce account to measure ROI on ads, campaigns, and keywords in Google Analytics ."
author = "Attributio"
aliases = [
    "/blog/2018/11/21/the-ultimate-guide-to-measure-roi-on-your-direct-marketing-efforts-with-salesforce-and-google-analytics-1/",
    "/blog/2018/12/05/the-ultimate-guide-to-measure-roi-on-your-direct-marketing-efforts-with-salesforce-and-google-analytics-2/",
    "/the-ultimate-guide-to-measure-roi-on-your-direct-marketing-efforts-with-salesforce-and-google-analytics-2/"
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

If you would like a demonstration of collecting analytics for your leads, <a href="/meet/">book a demo here</a>.
