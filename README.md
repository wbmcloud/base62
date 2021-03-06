## WARNING! This package is no longer maintained!

# Base62 Algorithm

![base62-package](https://cloud.githubusercontent.com/assets/499192/7440616/09e67fa8-f0c0-11e4-83e6-06e785883cae.png)

A reversible base62 ID obfuscater. Works well with [Laravel](https://github.com/laravel/laravel).

```php
// The base string.
$string = '0123456789abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ';

// Setup the Base62 instance.
$base = new Base62($string);

// Encode an integer.
$base->encode(4815162342); // returns '5fRVGK'

// Decode a string.
$base->decode('5fRVGK'); // returns 4815162342
```

[![Build Status](https://img.shields.io/travis/vinkla/base62/master.svg?style=flat)](https://travis-ci.org/vinkla/base62)
[![StyleCI](https://styleci.io/repos/15844313/shield?style=flat)](https://styleci.io/repos/15844313)
[![Latest Version](https://img.shields.io/github/release/vinkla/base62.svg?style=flat)](https://github.com/vinkla/base62/releases)
[![License](https://img.shields.io/packagist/l/vinkla/base62.svg?style=flat)](https://packagist.org/packages/vinkla/base62)

## Installation
Require this package, with [Composer](https://getcomposer.org/), in the root directory of your project.

```bash
composer require vinkla/base62
```

## Laravel
If using [Laravel](http://laravel.com) **(not required)**, add the service provider to ```config/app.php``` in the providers array.

```php
'Vinkla\Base62\Base62ServiceProvider'
```

If you want you can use the [facade](http://laravel.com/docs/facades). Add the reference in ```config/app.php``` to your aliases array.
```php
'Base62' => 'Vinkla\Base62\Facades\Base62'
```

To add the configuration file to your `config` directory, run the command below.
```bash
php artisan vendor:publish
```

#### Looking for a Laravel 4 compatable version?

Please use [1.0 branch](https://github.com/vinkla/base62/tree/1.0) instead. Installable by requiring:

```bash
composer require vinkla/vimeo:~1.0
```

## Usage
Here you can see an example of just how simple this package is to use.

```php
use Vinkla\Base62\Base62;

// The base string.
$string = '0123456789abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ';

// Setup the Base62 instance.
$base = new Base62($string);

// Encode an integer.
$base->encode(4815162342); // returns '5fRVGK'

// Decode a string.
$base->decode('5fRVGK'); // returns 4815162342
```

## Laravel Usage
If you implement this package in a Laravel application, which isn't required, we've provided real world examples below.
```php
// You can alias this in config/app.php.
use Vinkla\Base62\Facades\Base62;

Base62::encode(4815162342);
// We're done here - how easy was that, it just works!

Base62::decode('5fRVGK');
// This example is simple and there are far more methods available.
```

If you prefer to use dependency injection over facades like me, then you can inject the manager:

```php
use Vinkla\Base62\Base62;

class Foo
{
	protected $base62;

	public function __construct(Base62 $base62)
	{
		$this->base62 = $base62;
	}

	public function bar()
	{
		$this->base62->decode('5fRVGK');
	}
}

App::make('Foo')->bar();
```

## License

Base62 package is licensed under [The MIT License (MIT)](LICENSE).
