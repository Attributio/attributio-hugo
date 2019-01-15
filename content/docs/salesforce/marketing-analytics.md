+++
title = "Salesforce Marketing Analytics App Documentation"
date = "2018-12-18"
description = "Instructions to download and install Attributio Marketing Analytics App integration with Google Analytics for Salesforce"
author = "Attributio"
+++


## Installation

Follow the link provided to you and select the option to "Install for All Users".

<img class="img-responsive img-thumbnail" src="/img/docs/salesforce/install-marketing-analytics-screen.png" alt="install salesforce marketing analytics attribution app" />

<br>

### Configure remote site settings in Salesforce

1. Navigate to Setup > Settings > Security > Remote Site Settings and create a new setting
	<br><br>
	<img class="img-responsive img-thumbnail" src="/img/blog/201812/sf-new-remote-site.png" alt="salesforce send revenue to google analytics" />

2. Add the following Remote Site URL: 
	<br><br>
	<code>https://www.google-analytics.com</code>
	<br><br>
	<img class="img-responsive img-thumbnail" src="/img/blog/201812/sf-new-remote-site-create.png" alt="salesforce send revenue to google analytics" />

<br>

## Configure Lead Mappings

1. Select Setup under the gear icon on the top right of your screen.
2. In the navigation pane to the left go to Platform Tools > Objects and Fields > Object Manager. 
3. Select Lead.
4. Select Fields & Relationships and on the top right corner, select Map Lead Fields.
5. Map GA Client ID, GA Revenue ID, GA Tracking ID, and GA User ID to their respective fields from Leads to Accounts and Opportunities.

<img class="img-responsive img-thumbnail" src="/img/docs/salesforce/map-leads-fields.png" alt="map leads fields for salesforce marketing analytics attribution app" />

<br>

## Configure Web-To-Lead Form

1. Navigate to Platform Tools > Feature Settings > Marketing > Web-to-Lead.
2. Create new form.
3. Add GA Client ID, GA Revenue ID, GA Tracking ID, and GA User ID to our new form and create.

	<img class="img-responsive img-thumbnail" src="/img/docs/salesforce/web-to-lead-setup.png" alt="create web to lead form salesforce attribution google analytics gclid" />

4. Modify the input fields for GA Client ID, GA Revenue ID, GA Tracking ID, and GA User ID by removing the the label, maxlength, and size fields and convert the input type field to hidden and add those fields to your form.
	* Before

	<img class="img-responsive img-thumbnail" src="/img/docs/salesforce/web-to-lead-setup-before.png" alt="create web to lead form salesforce attribution google analytics gclid before" />

	* After

	<img class="img-responsive img-thumbnail" src="/img/docs/salesforce/web-to-lead-setup-after.png" alt="create web to lead form salesforce attribution google analytics gclid after" />

5. You will need to use some javascript to retreive the client id from Google Analytics and add it to your hidden field. You can find detailed instructions <a href="/blog/2017/04/27/track-conversions-with-google-analytics-client-id/">here</a>.
6. You can manually set the values of GA Revenue ID & GA Tracking ID in the form.

## Configure Your GA Activity Link

In order to view your Lead's activity on your website via Google Analytics, you'll need to add a custom setting and add the custom link object provided by this app into your desired layout in Leads, Accounts, and Opportunities.

1. Find the unique path for visitor activity in Google Analytics
	* Log into Google Analytics
	* Navigate to Audience > User Explorer and select a random CLient ID
	* Note the ID in the url path after "visitors-user-activity"
	
	<img class="img-responsive img-thumbnail" src="/img/docs/salesforce/ga-visitor-user-activity-link.png" alt="google analytics visitor activity link id" />

2. Now in Salesforce, navigate to Platform Tools > Custom Code > Custom Settings
3. Select Manage for Attributio Settings
4. Select New and add the ID extracted from Google Analytics to GA Activity Link ID field in Salesforce Custom Settings

	<img class="img-responsive img-thumbnail" src="/img/docs/salesforce/ga-activity-link-id-setting.png" alt="google analytics visitor activity link id for salesforce" />	

5. Finally, add the GA Activity Link to a Page Layout under Platform Tools > Objects and Fields > Object Manager > {The object you want to add the link}> Page Layout
6. Drag and drop the GA Activity Link into the Custom Links section

	<img class="img-responsive img-thumbnail" src="/img/docs/salesforce/ga-activity-link-page-layout.png" alt="google analytics visitor activity custom link for salesforce" />

7. Finally, navigate to the view of your page layout and if you added the GA Activity Link ID under custom settings and your Object has an id for the GA Client ID field present, you should have a valid link to view the activity of that user in Google Analytics.

## Workflow

If the Marketing Analytics App has been properly configured, your website should be collecting the client id provided by Google Analytics and storing it as a custom field under Leads. During the Lead Conversion and Opportunity Qualification Proccess, you should be able to view all of the details regarding your Lead and Opportunity's activity on your website, from how they got there (what ads, keywords, campaigns, or referrals), to what pieces of content they visited before converting on your website form.

In addition, when an Opportunity is Won and the amount and client id fields are present, that revenue data will be available in custom reports in Google Analytics for further anaysis on determining ROI on Ads and Marketing campaigns.

## Versions

- v 1.0 First Release
- v 1.1 Removed Remote SIte Settings for manual installation by user.
