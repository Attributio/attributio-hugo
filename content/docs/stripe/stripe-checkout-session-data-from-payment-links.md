+++
title = "Stripe Checkout Session Data From Payment Links"
description = "Track attribution data for Stripe Payment Links by retrieving Stripe Checkout Session data to thank you redirect"
author = "Attributio"
anchors = ["introduction", "redirect", "api-key", "get-data"]
+++


## Stripe Checkout Session Data from Stripe Payment Links {#introduction}

Stripe continues to make transactions easier for anyone that wants to collect payments online. Anyone that signs up with Stripe can create a product and payment link and Stripe will handle the entire checkout process. This makes it fast and easy to start collecting payments by embedding payment links on your website, emails, or even SMS!

That's great for simple invoices where you know your customer but for marketers and entrepreneurs that want to quickly create a product and payment link and run marketing campaigns to gain traction need a little help with conversion tracking.

That's because by default, most tracking pixels like Google Analytics or affiliate programs requires a tag to be added on the site of origin when a conversion occurs with some information about the customer. The problem with Stripe Payment Links is that although you can redirect customers, the only data you can send back is the CHECKOUT_SESSION_ID. Ususally, analytics tools requries additional data like an email or transaction data to measure ROAS and attribution.

That's why we created <a href="https://stripe.attribut.io" target="_blank">a simple tool to help you get data from Stripe</a> with the CHECKOUT_SESSION_ID once you are redirected back to your thank you page.

## Redirect and Pass CHECKOUT_SESSION_ID to Thank You Page {#redirect}

We're going to assume that you aleady know how to how to create Products and Payments in Stripe.

The first thing you will need to do is to add the CHECKOUT_SESSION_ID parameter to your redirect link. You can <a href="https://stripe.com/docs/payments/payment-links#change-confirmation-behavior" target="_blank">read the docs for sending the CHECKOUT_SESSION_ID here</a>.

<img class="img-responsive img-thumbnail" src="/img/docs/stripe/stripe-confirmation-page-checkout-session-id.png" alt="add stripe checkout session id to confirmation redirect payment links" />

## Create Checkout Sessions API KEY {#api-key}

Now we need to create an api key exclusively for checkout sessions in Stripe and only provide read access. We do this to limit access to other sensitive data.

<img class="img-responsive img-thumbnail" src="/img/docs/stripe/create-stripe-checkout-sessions-api-key.png" alt="create stripe checkout sessions api key" />

Now we can use this <a href="https://stripe.attribut.io" target="_blank">app to use CHECKOUT_SESSION_ID and api key to get data from stripe</a> in the checkout.session.completed event.

Once you create an account, you can create a property with the hostname of your website where the Stripe Payment Link redirects to after payment and add your api key.

<img class="img-responsive img-thumbnail" src="/img/docs/stripe/stripe-app-to-get-checkout-session-data.png" alt="create property in app to interact with stripe checkout session data" />

## Call Server To Get Stripe Checkout Session Data {#get-data}

Once you create a property in the app, all you need to do is call your property from the host you added like so:

```javascript
if ({{Checkout Session ID}}) {
  var xhr = new XMLHttpRequest();
  xhr.onreadystatechange = function() {
    
    if (xhr.readyState == XMLHttpRequest.DONE) {
      var json = JSON.parse(xhr.responseText)
      if (json["customer_email"]) {
        sendConversion(json["customer_email"]);
      }

    }
  }
  xhr.open('GET', 'https://stripe.attribut.io/checkout/sessions.json?property_id={{Property ID}}&checkout_session_id={{Checkout Session ID}}', true);
  xhr.send(null);
}
```

If you make a call to the app from the current host with the proper Property ID and Checkout Session ID, you will get a response from the server with Stripe data that currently is limited to the customer_id and customer_email.

If you need access to additional data, you can make a request and we can add it.

And once you have your data you can send conversion data to your conversion tracking software whatever that may be.

If you need help bringing all of this together, <a href="/meet/">we’re here for that</a>.
