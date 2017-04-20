# Openfintech SDK
[![Build Status][ico-travis]][link-travis]
[![Quality Score][ico-code-quality]][link-code-quality]
[![Coverage Status][ico-scrutinizer]][link-scrutinizer]
[![Latest Version on Packagist][ico-version]][link-packagist]
[![Total Downloads][ico-downloads]][link-downloads]
[![Software License][ico-license]](LICENSE.md)

OpenFinTech.io is an open database that comprises of standardized primary data for FinTech industry.
It contains such information as geo-location data (countries, cities, regions), organizations, currencies (national, digital, virtual, crypto), banks, digital exchangers, payment providers (PSP), payment methods, etc.
It is created for communication of cross-integrated micro-services on "one language". This is achieved through standardization of entity identifiers that are used to exchange information among different services.
 
## Install 

To install the latest version of this library, run the command below:

```bash
$ composer require openfintech/php-sdk
```
This sdk uses [woohoolabs/yang](https://github.com/woohoolabs/yang)  library.

## Basic usage

#### Available resources:

1. Banks
1. Countries
1. Currencies
1. CurrencyIssuers
1. Exchangers
1. OrganizationIndustries
1. Organizations
1. PaymentMethods
1. PaymentMethodIssuers
1. PaymentProviders

```php

$organizationResource =  new \Oft\Client\Resources\Organizations();

$organizations = [];

$attributes = [];

// Get resource iterator

foreach ($organizationResource->getResources() as $organization) {

    $organizations[] = $organization->toArray();

    $attributes[] = $organization->attributes();
    
    $relationship = $organization->relationship('active_in_countries')->toArray();

}
```


Usage without service 
```
$apiService = new \Oft\Client\ApiService(\Oft\Client\Resources\Exchangers::RESOURCE_URL);
$elements = [];

$attributes = [];

foreach ($apiService->getResources() as $exchanger) {

    $elements[] = $exchanger->toArray();

    $attributes[] = $exchanger->attributes();

    $organizationData = $exchanger->relationship('organization')->toArray();

}
```
Get single resource 
```
$apiService = new \Oft\Client\ApiService(Oft\Client\Resources\Banks::RESOURCE_URL);

$bank = $apiService->getResource('bnk_PQeP6WNubMpqZqGa'); 

$bankArray = $bank->toArray();

$bankAttr  = $bank->attributes();


```
## Api documentation 

For more details go to official site [openfintech.io](https://api.openfintech.io)

## License

The MIT License (MIT). Please see [License File](LICENSE.md) for more information.

[ico-version]: https://img.shields.io/packagist/v/openfintech/php-sdk.svg?style=flat-square
[ico-license]: https://img.shields.io/badge/license-MIT-brightgreen.svg?style=flat-square
[ico-travis]: https://img.shields.io/scrutinizer/build/g/openfintechio/php-sdk.svg?style=flat-square
[ico-scrutinizer]: https://img.shields.io/scrutinizer/coverage/g/openfintechio/php-sdk.svg?style=flat-square
[ico-code-quality]: https://img.shields.io/scrutinizer/g/openfintechio/php-sdk.svg?style=flat-square
[ico-downloads]: https://img.shields.io/packagist/dt/openfintech/php-sdk.svg?style=flat-square

[link-packagist]: https://packagist.org/packages/openfintech/php-sdk
[link-travis]: https://scrutinizer-ci.com/g/openfintechio/php-sdk
[link-scrutinizer]: https://scrutinizer-ci.com/g/openfintech/php-sdk/code-structure
[link-code-quality]: https://scrutinizer-ci.com/g/openfintech/php-sdk
[link-downloads]: https://packagist.org/packages/openfintech/php-sdk
[link-author]: https://github.com/openfintechio
[link-contributors]: ../../contributors
