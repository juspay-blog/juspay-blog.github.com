---
layout: post
title: "Introducing Juspay's Express Checkout as a Service"
description: "Express Checkout Service offered by Juspay"
category: 
tags: [express checkout, online payments, e-commerce]
---
{% include JB/setup %}

![Express Checkout](/assets/images/chn_rail_crh2.jpg)

This is the picture of [CRH2](http://en.wikipedia.org/wiki/China_Railways_CRH2 "CRH2") high speed train in China. The maximum speed of this train is a whopping 350 km/h. Such high speed trains are not just technology marvel. These are symbols of efficiency. 

Every country puts a lot of effort to ensure that her citizens are literate and healthy. When people are healthy and smart, they are more productive and efficient. This in turn, makes a country prosperous. 

Just like a country, every ecosystem focuses on ensuring that its sub-systems are efficient. A great country needs a great economy. A great economy needs an efficient financial system. This brings us to the payments infrastructure issue. Just like good roads are required for efficient travel, a great payments infrastructure is required for efficient functioning of online economy. 
  
#### Express Checkout

![Express Checkout Form](/assets/images/express-checkout-form.png)
  
This is our first step to help increase the efficiency of online payment systems. In a typical online payments scenario, there are 7 steps involved before the checkout process is completed. Express Checkout reduces this to __2 simple steps__. From our analysis, we have also observed that express checkout takes __less than 15 seconds__ to complete a payment. 

HTTP Redirection based workflow will inevitably lead to dead ends at times. On the contrary, Express Checkout retains the customer on the checkout page until the completion of payment. The complicated redirection is offloaded to a separate window.This reduces the frustration level for the customer, should the payment operation fail, for whatever reasons technical or non-technical. The net effect is that satisfaction levels of customers increase. 

A typical merchant faces about [65% of shopping cart abandonment](http://www.invesp.com/blog/cro/shopping-cart-abandonment-rate-statistics-infographic.html "65% of shopping cart abandonment"). Express Checkout helps improve the situation. An approximate estimate on how much a business can benefit from this solution can be found [here](https://merchant.juspay.in/gain/ "Shopping Cart Improvement").


#### How it works

Juspay will store credit card (or debit card) information of buyers on behalf of partner merchants. Card information is stored only after the customer provides his/her consent. Note that we are PCI Level 1 Compliant and are fully authorized to store card information. 

![Inline Checkout Form](/assets/images/inline-checkout-form.png)

The first time checkout will be a regular one, as shown above. During the subsequent purchase, the merchant can obtain the tokenized card information of customer from Juspay through our simple APIs. Only CVV number is required from the customer at this point. Customer enters this 3 digit code and proceeds to 3D Secure step and subsequently completes payment. 

The payment instruction is sent to bank from Juspay's secure infrastructure, but on behalf of the merchant. Thus, the money doesn't flow through Juspay but rather is routed directly to the merchant's account.

#### Simple APIs

Our foundation APIs are completely HTTP based. We have consciously designed the APIs to be very minimalistic. These APIs accept regular HTTP payload (form-url-encoded) and talk back in JSON. Listed below are our APIs to create an order and list cards pertaining to customer.

<pre class="prettyprint linenums lang-html">

# Create an order

curl https://api.juspay.in/init_order \
    -u 880E8EC5B9CA4450BD37ABB6E3CB2FED: \
    -d "amount=400.00" \
    -d "order_id=testuser3_ord_110011" \
    -d "customer_id=testuser3_user_101" \
    -d "customer_email=customer@mail.com" \
    
# List cards pertaining to a customer

curl https://api.juspay.in/card/list \
    -u 880E8EC5B9CA4450BD37ABB6E3CB2FED: \
    -d "customer_id=sindbad" \

</pre>

Merchants are free to design the credit card form in whichever manner they prefer. Our integration script is as small as that of Google Analytics! 

<pre class="prettyprint linenums lang-html">&lt;script type="text/javascript" 
    src="https://api.juspay.in/pay.js"&gt;&lt;/script&gt;

// The payment form goes here.
&lt;script type="text/javascript"&gt;
    Juspay.Setup({
        payment_form: "#payment_form",
        success_handler: function(status) {},
        error_handler: function(error_code, error_message, bank_error_code, bank_error_message, gateway_id) {}
    })
&lt;/script&gt;
</pre>

These are few examples. Our entire system is developed keeping simplicity as the foremost principle. From our past experience we have seen that simple things always have the capability to scale very nicely. Although we presently do not operate at a very large scale, we have tested the capabilities of our systems to scale without sacrificing throughput. 

#### Inspiration

A great amount of our design and philosophy is inspired from Amazon, Cleartrip, Square, Stripe and Flipkart. We are proud to stand on the shoulders of these giants. Our mission is to simplify online payments in India. We sincerely hope and believe that we would be able to help the ecosystem move forward. 

#### Who can use it

Express Checkout can only work in a trusted environment. So we recommend this solution only for merchants who have brand recognition and enjoy a certain level of customer trust. Merchants serving niche categories with significant number of repeat customers can also benefit from this solution.

Upcoming merchants are encouraged to try our [Inline Checkout](https://merchant.juspay.in/merchant/inline-checkout-demo "Inline Checkout") solution. This product has all the benefits but for card storage. 

For any queries, reach out to us by shooting a mail to [info@juspay.in](mailto:info@juspay.in). Please also follow us at [@juspay](http://twitter.com/juspay) for interesting updates. 