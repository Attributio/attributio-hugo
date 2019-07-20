+++
title = "Do Paid Ads Really Work?"
date = "2019-07-02"
tags = ["advertising, google, attribution"]
categories = ["attribution"]
banner = "/img/blog/201907/adspend.png"
keywords = "conversion attribution for paid advertising, conversion attribution for google search, paid advertising vs content marketing, who gets credit for conversions"
description = "Advertising vs content marketing: who gets credit for conversions?"
author = "Attributio"
aliases = [
    "/blog/2019/07/02/do-paid-ads-really-work/"
]
+++


## What Channels Convert?

If you've dabbled in digital advertising and content marketing, you might find that your advertisers' attribution reports don't line up. That's because they want credit for your conversions so you'll spend more on their platforms.

If you've ever looked at a Google Analytics report, you'll find that either you have a lot of Direct traffic or if you have some content, you get a lot of conversions through Organic traffic. The problem with these reports is that attribution is often defined within a 30 day window and attribution is based on a last-click model so you'll never really know where your visitors originated from.

### Branded Search Filtering

You might have created Branded Paid Search Ads on Adwords to separate visitors that are aware of your Brand. But that doesn't tell you where your customers actually come from. You might have even gone the extra mile and created custom Channel Groupings for your Organic Searches to exclude keywords from your brand. If so, kudos to you.

If you've done any of the above, you'll discover that a lot of your conversions aren't actually coming from your CPC campaigns or even from your Organic searches since these customers are already aware of your brand and are deliberately searching for you with a higher intent to convert. And quite frankly, even when we add a Branded Organic Search Channel in Google Analytics, we can never be quite certain if Google makes all of your branded keywords available to filter out in the first place.

## Own Your Analytics

A better approach to segmenting your conversions for Channels that bring in new customers, is to collect your own analytics. You don't have to implement any complex database to store Analytics and pay an exhorbitant amount of money to build out an analytics system. All you need to do is to store your visitors' session data on their browser and store that data when your visitors convert.

### What Data to Store

You don't want to store too much data on your visitors' browser but you want enough information to help you make better decisions about where to allocate your marketing budget. So what data should you store? The standard utm parameters that you tag on all your campaigns is a start and you can add additional data like page visits, session duration, and location data should you find it relevant (<a href="/docs/attributio/defining-attribution-parameters/">See here for more</a>). The key is to store the data that is relevant to you based on the sessions that are relevant and leaving out things that don't matter like Direct Sessions and Branded Searches.

### Landing Page Based Segmentation

You can go one extra step by storing referrer data and using that to determine whether a person visited your site based on whether they visited your homepage or a content related page. By doing this, you can get extra information that Google won't give you -- keyword data. Since Google doesn't like to share keyword data for Organic Searches, you can work backwords by determining which keywords certain pages on your site are most prominent and attribute those visits to those keywords rather than visitors that were already brand aware.

You can ignore First Interaction or Last Interaction Session data that includes Google Organic Searches as a source and medium by determining if they visited your homepage vs if they visited a content related page first. You could even ignore entirely any sessions that include the homepage as a landing page if the source and medium is google/organic. By doing this, you reduce the amount of data you store on your visitors' browsers and you can more easily filter through sessions to assign attribution.

## Sifting Through Sessions

Now this is where things get interesting. You can do a whole lot of analysis with the session data that you store. Typically collecting First and Last Interaction Session data is way more than companies typically have at their disposal but if you spend a significant amount of money on advertising, you're going to want more. You could, for example, give weighted scores to sources, mediums, campaigns, and even keywords to all of the relevant sessions that assisted in conversions and you could even apply your own filters to determine which channels should be given more weight.

These reports take time to set up but the most important part of the puzzle is to implement your analytics strategy so that you have enough data to make sense of your conversions. And if you need help, <a href="/meet/">we're here for that</a>.

