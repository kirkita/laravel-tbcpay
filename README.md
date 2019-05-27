# Laravel TbcPay

This package allows you to use TBC payments in your Laravel application.

## Table of Contents

- [Installation](#installation)
- [Generating and placing a certificate](#generating-and-placing-a-certificate)

## Installation

```
composer require lotuashvili/laravel-tbcpay
```

#### For Laravel <= 5.4

If you're using Laravel 5.4 or lower, you have to manually add a service provider in your `config/app.php` file.
Open `config/app.php` and add `TbcPayServiceProvider` to the `providers` array.

```php
'providers' => [
    # Other providers
    Lotuashvili\LaravelTbcPay\TbcPayServiceProvider::class,
],
```

Then run:

```
php artisan vendor:publish --provider="Lotuashvili\LaravelTbcPay\TbcPayServiceProvider"
```

### Generating and placing a certificate

TBC provides SSL certificate in **.p12** format, we need to transform it to **.pem** format. Use command below:

```
openssl pkcs12 -in *.p12 -out tbcpay.pem
```

After transformation, place certificate (**.pem** file) in `storage/certificates` folder. Name it whatever you want (tbcpay.pem in this example) and specify the name and password in `.env`

### Environment

Set your environment variables:

**Note:** Specify only certificate file name instead of full path. Certificates are placed in `storage/certificates` folder

Set default currency with ISO 4217 standart. List of all currencies: http://en.wikipedia.org/wiki/ISO_4217 (Default is 981 - GEL)

```
TBCPAY_DEBUG=true
TBCPAY_CERTIFICATE_NAME=tbcpay.pem
TBCPAY_CERTIFICATE_PASS=YourPassword123
TBCPAY_DEFAULT_CURRENCY=981
```
