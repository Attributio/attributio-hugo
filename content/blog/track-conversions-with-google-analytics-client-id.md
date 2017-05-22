+++
title = "Track Conversions With Google Analytics' Client ID"
date = "2017-04-27"
tags = ["google analytics"]
categories = ["tutorial"]
banner = "/img/blog/201704/session_based_client_id.png"
keywords = "google analytics conversion tracking, google analytics attribution, custom attribution model with google analytics"
description = "Use avaialble cookies in Google Analytics to track your customer's behavior along with their conversions from the source."
+++


## Introduction

Google Analytics is an underutilized tool and there are a few basic things you can do to gain more insight into your conversions. Last year in March of 2016 Google made their new [User Explorer](https://support.google.com/analytics/answer/6339208?hl=en) available to the public. It's a great tool but unfortunately, you can't drill down into other dimensions with this tool yet. 

What the User Explorer essentially does is aggregate users based on the client id that google collects in the form of a cookie set in your visitor's browser. Also, you can't combine this information with other dimensions or metrics like where the user came from.

## Why You Need to Add Client ID Now

When you're ready to start looking at where your conversions are coming from, you'll want to connect the information related to where they came from and how they interacted with your site. Unfortunately, you wont have that data. And you'll have to wait until you've collected enough data to make any kind of assessment on conversions.

For example, if you decide to run an ad campaign and spend $10k on cpc, if you want to see the results at the end of the month and you only have a basic analytics setup, you'll have a difficult time connecting your converted users to all the little interactions that visitor had with the various ads you ran along with their activity on your website. And if there's a big chunk of your conversions that isn't trackable, you'll have a harder time mazimizing every single dollar of your marketing budget.

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

You'll want to add the following code as an ammendment to the default embed code that Google Analytics provides. So if you have the default Universal Analytics snippet installed on your website, you'll want to modify it like so:

*Before*

```javascript
(function(i,s,o,g,r,a,m){i['GoogleAnalyticsObject']=r;i[r]=i[r]||function(){
(i[r].q=i[r].q||[]).push(arguments)},i[r].l=1*new Date();a=s.createElement(o),
m=s.getElementsByTagName(o)[0];a.async=1;a.src=g;m.parentNode.insertBefore(a,m)
})(window,document,'script','https://www.google-analytics.com/analytics.js','ga');

ga('create', 'UA-XXXXXXX-1', 'auto');
ga('send', 'pageview');

```

*After*

```javascript
(function(i,s,o,g,r,a,m){i['GoogleAnalyticsObject']=r;i[r]=i[r]||function(){
(i[r].q=i[r].q||[]).push(arguments)},i[r].l=1*new Date();a=s.createElement(o),
m=s.getElementsByTagName(o)[0];a.async=1;a.src=g;m.parentNode.insertBefore(a,m)
})(window,document,'script','https://www.google-analytics.com/analytics.js','ga');

ga('create', 'UA-XXXXXXX-1', 'auto');
ga(function(tracker) {
  var clientId = tracker.get('clientId');
  ga('set', 'dimension1', clientId);
  ga('send', 'pageview');
});
```
## Need Help Setting Up Your Custom Dimensions?

Sometimes it's not always so simple to configure custom dimensions. Your developer may have set up your analytics in a custom way ot you might be using Google Tag Manager to manage all of your js snippets.

In that case, we have experts standing by to [install your custom dimesions. Meet Your Expert Today!](/join/)

