## Laravel service provider for PHP Console

PHP Console allows you to handle PHP errors & exceptions, dump variables, execute PHP code remotely and many other things using [Google Chrome extension PHP Console](https://chrome.google.com/webstore/detail/php-console/nfhmhhlpfleoednkpnnnkolmclajemef) and [PhpConsole server library](https://github.com/barbushin/php-console).

This packages integrates [PHP Console server library](https://github.com/barbushin/php-console) with [Laravel framework](http://laravel.com) as configurable service provider.

## Installation

Require this package in Laravel project `composer.json` and run `composer update`

    "php-console/laravel-service-provider": "1.*"

After updating composer, add the service provider line to the begining of `providers` array in `/app/config/app.php`

	'providers' => array(
		'PhpConsole\Laravel\ServiceProvider',

## Edit config

PHP Console service provider config-file looks like this:

	return array(
		'isEnabled' => true,
		'handleErrors' => true,
		'handleExceptions' => true,
		'sourcesBasePath' => base_path(),
		'registerHelper' => true,
		'serverEncoding' => null,
		'headersLimit' => null,
		'password' => null,
		'enableSslOnlyMode' => false,
		'ipMasks' => array(),
		'isEvalEnabled' => false,
		'dumperLevelLimit' => 5,
		'dumperItemsCountLimit' => 100,
		'dumperItemSizeLimit' => 5000,
		'dumperDumpSizeLimit' => 500000,
		'dumperDetectCallbacks' => true,
		'detectDumpTraceAndSource' => false,
	);

See [PhpConsole\Laravel\ServiceProvider](/src/PhpConsole/Laravel/ServiceProvider.php) for detailed options description.

By default it's located in `/vendor/php-console/laravel-service-provider/src/config/config.php` and it's not recommended to be edited in this path because it will be overwritten on next `composer update`. 

If you want to edit config you need to run

    php artisan config:publish php-console/laravel-service-provider

So config-file will be moved to `/app/config/packages/php-console/laravel-service-provider/config.php` and can be edited as you want and changes will not be lost after `composer update`.
