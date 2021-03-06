# Laravel Uuid

[![Total Downloads](https://poser.pugx.org/webpatser/laravel-uuid/downloads.svg)](https://packagist.org/packages/webpatser/laravel-uuid)
[![Build Status](https://secure.travis-ci.org/webpatser/laravel-uuid.png?branch=master)](http://travis-ci.org/webpatser/laravel-uuid)
[![Latest Stable Version](https://poser.pugx.org/webpatser/laravel-uuid/v/stable.svg)](https://packagist.org/packages/webpatser/laravel-uuid)
[![Latest Unstable Version](https://poser.pugx.org/webpatser/laravel-uuid/v/unstable.svg)](https://packagist.org/packages/webpatser/laravel-uuid)


Laravel package to generate a UUID according to the RFC 4122 standard. Support for version 1, 3, 4 and 5 UUID are built-in.


## Installation

Add `webpatser/laravel-uuid` to `composer.json`.

    "webpatser/laravel-uuid": "1.*"
    
Run `composer update` to pull down the latest version of Country List.

Edit `app/config/app.php` and add the `alias`

    'aliases' => array(
        'Uuid' => 'Webpatser\Uuid\Uuid',
    )

    
## Basic Usage

To quickly generate a UUID just do

	Uuid::generate()
	
This will generate a version 1 with a random ganerated MAC address.

## Advanced Usage

### UUID creation

Generate a version 1, time-based, UUID. You can set the optional node to the MAC address. If not supplied it will generate a random MAC address.

	Uuid::generate(1,'00:11:22:33:44:55');
	
Generate a version 3, name-based using MD5 hashing, UUID

	Uuid::generate(3,'test','6ba7b810-9dad-11d1-80b4-00c04fd430c8');
	
Generate a version 4, truly random, UUID

	Uuid::generate(4);

Generate a version 5, name-based using SHA-1 hashing, UUID

	Uuid::generate(5,'test','6ba7b810-9dad-11d1-80b4-00c04fd430c8');
	
### Some magic features

To import a UUID
	
	$uuid = Uuid::import('d3d29d70-1d25-11e3-8591-034165a3a613');
	
Extract the time for a time-based UUID (version 1)

	$uuid = Uuid::generate(1);
	dd($uuid->time);
	
Extract the version of an UUID

	$uuid = Uuid::generate(4);
	dd($uuid->version);

	
## Notes

Full details on the UUID specification can be found [here](http://tools.ietf.org/html/rfc4122)

If used on windows it will use the [CAPICOM getRandom method]('http://msdn.microsoft.com/en-us/library/aa388182(VS.85).aspx')