+++
title = "Defining Attribution Parameters"
description = "Options for defining attribution"
author = "Attributio"
anchors = ["sessions", "definitions", "fields", "custom-fields", "custom sessions", "requirements", "google-analytics"]
+++


## Sessions

The most common type of session is <a href="https://support.google.com/analytics/answer/2731565?hl=en" target="_blank">defined by Google</a> based on time or by a change in campaign. In Google Analytics a new session is created during 30 minutes of inactivity.

By default, our sessions are not based on time so you may see session durations in excess of days. This is to minimize the amount of data stored in your visitor's browsers regarding their session data and not storing additional data for every visit past 30 minutes of inactivity if the source, medium, or campaign has not changed. This means that you will see a limited amount of direct traffic as a source in your conversions.

### Definitions

Our definition of a session is based on First and Last Interaction data and is based on a change of either of the following:

1. A change in source
2. A change in medium
3. A change in campaign

URL parameters utilize the same "utm_" structure that Google Analytics recommends. You can use a <a href="https://ga-dev-tools.appspot.com/campaign-url-builder/">free tool</a> to do the same.

### Default Fields

 <table class="table table-sm table-borderless">
 	<tr>
 		<td>First Interaction Referrer</td>
 		<td>Last Interaction Referrer</td>
 	</tr>
 	<tr>
 		<td>First Interaction Source</td>
 		<td>Last Interaction Source</td>
 	</tr>
 	<tr>
 		<td>First Interaction Medium</td>
 		<td>Last Interaction Medium</td>
 	</tr>
 	<tr>
 		<td>First Interaction Campaign</td>
 		<td>Last Interaction Campaign</td>
 	</tr>
 	<tr>
 		<td>First Interaction Content</td>
 		<td>Last Interaction Content</td>
 	</tr>
 	<tr>
 		<td>First Interaction Term</td>
 		<td>Last Interaction Term</td>
 	</tr>
 	<tr>
 		<td>First Interaction Landing Page</td>
 		<td>Last Interaction Landing Page</td>
 	</tr>
 	<tr>
 		<td>First Interaction Session Duration</td>
 		<td>Last Interaction Session Duration</td>
 	</tr>
 	<tr>
 		<td>First Interaction Page Visits</td>
 		<td>Last Interaction Page Visits</td>
 	</tr>
 </table>

### Custom Fields

Include additionals fields as follows:

- Journey By Source
- Journey By Medium
- Journey By Campaign
- Exclude Sources
- Exclude Mediums
- Exclude Campaigns
- Device
- Browser
- Location

## Custom Sessions

Often visitors convert after doing a branded paid or organic search. We typically do not want that information as attribution will typically be credited to Google where little weight should be placed. In these cases, we can set conditions to ignore certain paid branded clicks as Last Impressions and store the previous session with more valuable data.

There are many scenarios you can imagine for a custom fit attribution model for your company.

## Requirements

It is recommended to use SSL for all traffic to your site. Ensure that all non-ssl links are redirected to a standard SSL encrypted version of your site either containing the subdomain www or not. 

If visitors to your site jump between non-encrypted and encrypted versions of your site or between subdomains, session data will not be consistent and original attribution data will be lost.

When configuring redirects, all url parameters must be retained. If they are lost on redirect, session data will not properly be stored.

## Google Analytics

We encourage the use of Google Analytics to compare attribution data stored in your CRM with our tool. Although our tool is independent of Google Analytics, Google Analytics has so much data available that we recommend using it in conjunction with our tool for comparisons. That is why we configure your Analytics to store unique visitor data based on ids provided by Google so you can have all the data you could ever need.

