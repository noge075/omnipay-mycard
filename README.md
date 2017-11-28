# Omnipay: MyCard

**MyCard driver for the Omnipay PHP payment processing library**

[Omnipay](https://github.com/thephpleague/omnipay) is a framework agnostic, multi-gateway payment
processing library for PHP 5.3+. This package implements MyCard support for Omnipay.

## Installation

Omnipay is installed via [Composer](http://getcomposer.org/). To install, simply add it
to your `composer.json` file:

```json
{
    "require": {
        "xxtime/omnipay-mycard": "~1.0"
    }
}
```

And run composer to update your dependencies:

    $ curl -s http://getcomposer.org/installer | php
    $ php composer.phar update

## Support Gateways

The following gateways are provided by this package:

* MyCard (MyCard Web Checkout)

For general usage instructions, please see the main [Omnipay](https://github.com/thephpleague/omnipay)
repository.

## Basic Usage


```php

// initialize
$config = [
    'appId'  => 'MyCard_ServiceId',
    'appKey' => 'MyCard_Key'
];
$gateway = Omnipay::create('MyCard');
$gateway->initialize($config);

// Send purchase request
$response = $gateway->purchase(
    [
        'amount'        => '1.00',
        'currency'      => 'TWD',
        'description'   => 'product description',
        'transactionId' => mt_rand(100000, 999999),
    ]
)->send();

// Process response
if ($response->isSuccessful()) {
    // doing something here
    print_r($response);
}
elseif ($response->isRedirect()) {
    // doing something here
    // $data = $response->getData();
    // $transactionReference = $response->getTransactionReference();
    $response->redirect();
}
else {
    echo $response->getMessage();
}

```


## Related

[Project Home Page](https://github.com/xxtime/omnipay-mycard)  
[MyCard Official Website](https://www.mycard520.com.tw)  


## Support

If you are having general issues with Omnipay, we suggest posting on
[Stack Overflow](http://stackoverflow.com/). Be sure to add the
[omnipay tag](http://stackoverflow.com/questions/tagged/omnipay) so it can be easily found.

If you want to keep up to date with release anouncements, discuss ideas for the project,
or ask more detailed questions, there is also a [mailing list](https://groups.google.com/forum/#!forum/omnipay) which
you can subscribe to.

If you believe you have found a bug, please report it using the [GitHub issue tracker](https://github.com/thephpleague/omnipay-paypal/issues),
or better yet, fork the library and submit a pull request.