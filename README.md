# Koboo Pay PHP client

## Introduction
This document describes how to integrate with KOBOO PAY Api in order to process mobile
money and credit card payments.

## Registration
To be able to user KOBOO PAY API, a registration is required. This can be done by filling out
the form in this url: https://my.koboopay.com/registration
Once the form completed and submitted, you will receive a confirmation email

## Account Activation
Once your application has been reviewed and approved, you will receive a notification email
with your credentials. You can then log in to your account using the url:
https://admin.koboopay.com

## API Key Generation
Once logged into your account, you can use the right menu and select “Profil” to generate an
API key.

Note that this will be the only time the API secret will be visible. Please copy it somewhere
where your application will be able to access it as it will be required to communicate with
KOBOO PAY API.

## Making API Calls
### Create a payment
```php
<?php

use Devscast\KobooPay\Client;
use Devscast\KobooPay\Data\Payment;
use Devscast\KobooPay\Data\Currency;
use Devscast\KobooPay\Data\PaymentRequest;
use Devscast\KobooPay\Data\PaymentResponse;

$koboo = new Client(identifier: '*******', secret: '******');

```


```php
<?php

$payment = PaymentRequest::fromArray(merchantId: "GCO552", [
    'amount' => 10,
    'currency' => Currency::USD(),
    'description' => 'Basketball Shoes size 39 for kids',
    "firstName" => "Patrick",
    "lastName" => "Ngoy", 
    "email" => "pngoy@fakeemail.com",
    "phone" => "+24312345678",
]);

$result = $koboo->createPayment($payment);

var_dump($result); // instance of PaymentResponse
```

### View payment
```php
<?php

$result = $koboo->getPayment(
    reference: "7ec7d709-46a7-4845-936f-97bde3bf20cd", 
    payerReference: "8EBK-Z53"
);

var_dump($result); // instance of Payment
```

## contributors

<a href="https://github.com/devscast/koboo-pay/graphs/contributors">
  <img src="https://contrib.rocks/image?repo=devscast/koboo-pay"/>
</a>

### Suivez nous

We're social:

- [@DevscastTech](https://twitter.com/devscasttech) on Twitter.
- [Devscast](https://www.linkedin.com/company/devscast/) on LinkedIn 
- [@devscast.tech](https://www.instagram.com/devscast.tech/) on Instagram.
- [devscast.tech](https://web.facebook.com/devscast.tech/) on Facebook.
- [Devscast](https://www.youtube.com/channel/UCsvWpowwYtjfgS1BOcrX0fw) on Youtube.
- [devscast.tech](https://www.tiktok.com/@devscast.tech) on Tiktok.
