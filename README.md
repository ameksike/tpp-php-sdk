# TropiPay SDK PHP
TropiPay [SDK](https://packagist.org/packages/tonykssa/tpp-sdk) for PHP.

## Install 
- composer init
- composer require tonykssa/tpp-sdk

## Example 
- Create demo.php file: 
```php

// loading library
require_once __DIR__.'/vendor/autoload.php';
use TppSdk\TropiPay as TropiPay;

// define credentials
$clientId = "5aca1638f7596bee9cb388e51d2ad58e";
$clientSecret = "4a0150d3cec2036b9f24ec53f52e7c19";

// define the environment to use (production, development, test, etc.)
$enviroment = "develop";

// instantiate the library
$srv = new TropiPay($clientId, $clientSecret, $enviroment);

// define the data of the payment link to create
$payload = array(
    "reference"=> "my-paylink-1",
    "concept"=> "Bicycle",
    "favorite"=> "true",
    "amount"=> 3000,
    "currency"=>"EUR",
    "description" => "Two wheels",
    "singleUse"=>"true",
    "reasonId"=>4,
    "expirationDays"=>1,
    "lang"=>"es",
    "urlSuccess"=>"https://webhook.site/680826a5-199e-4455-babc-f47b7f26ee7e",
    "urlFailed"=>"https://webhook.site/680826a5-199e-4455-babc-f47b7f26ee7e",
    "urlNotification"=>"https://webhook.site/680826a5-199e-4455-babc-f47b7f26ee7e",
    "serviceDate"=>"2021-08-20",
    "client"=> array(
        "name"=>"John",
        "lastName"=>"McClane",
        "address"=>"Ave. Guadí 232, Barcelona, Barcelona",
        "phone"=>"+34645553333",
        "email"=>"client@email.com",
        "countryId"=>1,
        "termsAndConditions"=>"true"
    ),
    "directPayment"=>"true"
);

// create payment link
$paylink = $srv->createPaylink($payload);
```
- php demo.php