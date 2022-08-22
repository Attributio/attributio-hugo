+++
title = "Track Conversions With Google Analytics' Client ID & User ID"
date = "2017-04-27"
lastmod = "2019-07-25"
tags = ["google analytics"]
categories = ["tutorial"]
banner = "/img/blog/201704/session_based_client_id.png"
keywords = "google analytics client id, client id google analytics, google client id, clientid google analytics, client id in google analytics, get google analytics client id, client id google"
description = "Google Analytics provides a unique session id called the Client ID that you can use to track individual visitors in your conversion forms."
author = "Attributio"
aliases = [
    "/blog/2017/04/27/track-conversions-with-google-analytics-client-id/",
    "/track-conversions-with-google-analytics-client-id-and-user-id/"
]
+++


Google Analytics is an underutilized tool and there are a few basic things you can do to gain more insight into your conversions. Last year in March of 2016 Google made their new <a href="https://support.google.com/analytics/answer/6339208?hl=en" target="_blank">User Explorer</a> available to the public. It's a great tool but unfortunately, you can't drill down into other dimensions with this tool yet. Also, you can't combine this information with other dimensions or metrics like where the user came from.

<br>

<img class="img-responsive img-thumbnail" src="/img/blog/201704/user-report.png" alt="google analytics client id user report" />

<br>

What the User Explorer essentially does is aggregate users based on the client id that google collects in the form of a cookie set in your visitor's browser. Google uses this cookie internally but doesn't make it accessible to Google Analytic's users. The only way to access the client id is by exposing it and sending it to your Google Analytics property as a custom dimension.

<br>

<img class="img-responsive img-thumbnail" src="/img/blog/201704/user-list.png" alt="google analytics client id user report list" />

<br>

## Why You Need to Add Client ID Now

When you're ready to start looking at where your conversions are coming from, you'll want to connect the information related to where they came from and how they interacted with your site. Unfortunately, you wont have that data. And you'll have to wait until you've collected enough data to make any kind of assessment on conversions.

<br>

<img class="img-responsive img-thumbnail" src="/img/blog/201704/zoho-client-id.png" alt="google analytics client id in zoho crm" />
<div class="text-center small">Data collected in a CRM with custom session data and outgoing link to Google Analytics User Explorer</div>
<hr>

Assuming that you are collecting your visitor's client id when they convert, you can query as far back as you like on that user to visualize every step they took to convert. You can also view all of the channels that they navigated to before converting.

## How to Add Client ID as a Custom Dimension

You can add the client ID as a custom diemsion in google analytics by navigating to the admin section of your account and selecting the web property you want to modify/

<br>

<img class="img-responsive img-thumbnail" src="/img/blog/201704/property_custom_definitions.png" alt="add custom dimension to google analytics" />

<br>

Select Custom Definitions / Custom Dimensions and click on the "New Custom Dimension" button.

<br>

<img class="img-responsive img-thumbnail" src="/img/blog/201704/custom_dimensions_new.png" alt="add client id to google analytics" />

<br>

You want to add the name "Client ID" and set the scope to Session. You can add it as a Hit or User if you like but Session based granularity is appropriate since a session encompasses hits when a visitor interacts with your site and user based collection might miss some session interactions you'll want to observe at a later time.

<br>

<img class="img-responsive img-thumbnail" src="/img/blog/201704/session_based_client_id.png" alt="add session based client id to google analytics" />

<br>

Then you can set the custom dimesion value to your website according to the dimension id that google provides.

<br>

<img class="img-responsive img-thumbnail" src="/img/blog/201704/client_id_embed.png" alt="add custom dimension client id to website embed code" />

<br>

You'll want to add the following code as an ammendment to the default embed code that Google Analytics provides. So if you have the default Universal Analytics snippet installed on your website, you'll want to modify it as shown in the examples below. You can also see the [documentation provided by google](https://developers.google.com/analytics/devguides/collection/analyticsjs/cookies-user-id#getting_the_client_id_from_the_cookie).

### Universal Analytics Implementation of Client ID

*Before*

```javascript
ga('create', 'UA-XXXXXXX-1', 'auto');
ga('send', 'pageview');

```

*After*

```javascript
ga('create', 'UA-XXXXXXX-1', 'auto');
ga(function(tracker) {
  var clientId = tracker.get('clientId');
  ga('set', 'dimension1', clientId);
  ga('send', 'pageview');
});
```

You also have the option of sending the client id as a non-interaction event via Google Analytics like so:

```javascript
ga('create', 'UA-XXXXXXX-1', 'auto');
ga(function(tracker) {
  var clientId = tracker.get('clientId');
  tracker.set({dimension1: clientId});
  tracker.send('event', {
    nonInteraction: true
  });
});
```


### Gtag Implementation of Client ID

*Before*

```javascript
gtag('config', 'UA-XXXXXXX-1');

```

*After*

```javascript
gtag('config', 'UA-XXXXXXX-1', {
  'custom_map': {
    'dimension1': 'clientId'
  }
});
```

### Google Tag Manager Implementation of Client ID

You have the option of either setting a field with the name customTask and adding the code to extract the client id in your Google Analytics Setting Variable or to send the client id as a non-interaction event on all Window Loaded Page Views.

<br>

<img class="img-responsive img-thumbnail" src="/img/blog/201704/gtm-clientid.png" alt="add client id to google analytics" />

<br>

To set the customTask field, create a custom javascript variable and add the code as follows:

```javascript
function() {
  return function(model) {
    model.set('dimension2', model.get('clientId'));
  }
}
```

To set as a non-interaction event, create a custom javascript variable like so:

```javascript
function() {
  try {
    var trackers = ga.getAll();
    var i, len;
    for (i = 0, len = trackers.length; i < len; i += 1) {
      if (trackers[i].get('trackingId') === {{GA Property ID}}) {
        var clientId = trackers[i].get('clientId');
        return clientId;
      }
    }
  } catch(e) {
  	return '(not set)';
  }
}
```

## Difference Between Client ID and User ID

Depending on whether you have an authenitcation system on your website, you may have the added option of tracking your users. The benefit of doing so in the context of attribution is that you can stitch cross device sessions together. By default Google Analytics separates "Users" based on the cookies that it sets in your visitor's browsers (Our beloved Client ID). But in an age of multiple device usage, it leaves a big hole in proper attribution techniques.

If you have an optinon to also send User ID data to Google Analytics for tracking, it's a must for in-depth attribution techniques.

Google Analytics has an option where you can set an id for Users in the the admin section under Property > Tracking Info > User-ID.

<br>

<img class="img-responsive img-thumbnail" src="/img/blog/201704/ga-userid-setting.png" alt="add client id to google analytics" />

<br>

What you get is an additional View where you can track the behavior of your logged-in users. Unfortunately, it doesn't automatically stitch all of the activity of a particular browser with another browser when a user is logged in. You can see more in [google's documentation for user id here](https://support.google.com/analytics/answer/6205850?hl=en).

You will need to do this manually by not only setting the userID field in Google Analytics but also creating a custom dimension for User ID and sending that data alongside the standard configuration variable for User ID provided by Google Analytics so you can query that data at a later time.

What you end up with is the option of pulling User ID and Client ID from Google Analytics and tracking all of the sessions for a particular user. Where once you had a dark void of direct sessions, you can now extract additional session data from all of the devices that your users used to log in to your site.

## Need Help Setting Up Your Custom Dimensions?

Sometimes it's not always so simple to configure custom dimensions. Your developer may have set up your analytics in a custom way ot you might be using Google Tag Manager to manage all of your js snippets.

If you need help to [install your custom dimesions. Talk to an expert today](/meet/)