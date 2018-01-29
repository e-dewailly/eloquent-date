# Eloquent-Date

[![Latest Version][ico-version]](https://packagist.org/packages/seiler/eloquent-date)
[![Software License][ico-license]](LICENSE.md)

This package is the fork of seiler/eloquent-date.

This trait replaces Carbon with [Jenssegers\Date](https://github.com/jenssegers/date) in Laravel's Eloquent model.

Jenssegers\Date extends [Carbon](https://github.com/briannesbitt/Carbon) with multi-language support. Methods such as `format`, `diffForHumans`, `parse`, `createFromFormat` and the new `timespan`, will now be translated based on your locale.

This package is compliant with [PSR-1], [PSR-2] and [PSR-4].
If you notice compliance oversights, please send a patch via pull request.

[PSR-1]: https://github.com/php-fig/fig-standards/blob/master/accepted/PSR-1-basic-coding-standard.md
[PSR-2]: https://github.com/php-fig/fig-standards/blob/master/accepted/PSR-2-coding-style-guide.md
[PSR-4]: https://github.com/php-fig/fig-standards/blob/master/accepted/PSR-4-autoloader.md

## Laravel compatibility

 Laravel | Eloquent-Date
:--------|:--------
 5.5     | 5.5
 5.4     | 5.4
 
## Installation

Install using composer:

```bash
$ composer require seiler/eloquent-date
```

If you want to use Jenssegers\Date in other part of your application, there is a service provider included in the package [for integration](https://github.com/jenssegers/date#laravel) with the Laravel framework. This provider will get the application locale setting and use this for translations. To register the service provider, add the following to the providers array in `config/app.php`:

```php
'providers' => [
    ...
    /*
     * Application Service Providers...
     */
    Jenssegers\Date\DateServiceProvider::class,
    ...
];
```

You can also add it as a Facade in `config/app.php`:

```php
'aliases' => [
    ...
    'Date' => Jenssegers\Date\Date::class,
    ...
];
```

## Languages

The Date package contains language files for the following languages:

 - Albanian
 - Arabic
 - Azerbaijani
 - Bangla
 - Basque
 - Brazilian Portuguese
 - Bulgarian
 - Catalan
 - Croatian
 - Chinese Simplified
 - Chinese Traditional
 - Czech
 - Danish
 - Dutch
 - English
 - Esperanto
 - Estonian
 - Finnish
 - French
 - Galician
 - Georgian
 - German
 - Greek
 - Hebrew
 - Hindi
 - Hungarian
 - Icelandic
 - Indonesian
 - Italian
 - Japanese
 - Kazakh
 - Korean
 - Latvian
 - Lithuanian
 - Macedonian
 - Malay
 - Norwegian
 - Polish
 - Portuguese
 - Persian (Farsi)
 - Romanian
 - Russian
 - Thai
 - Serbian (latin)
 - Serbian (cyrillic)
 - Slovak
 - Slovenian
 - Spanish
 - Swedish
 - Turkish
 - Turkmen
 - Ukrainian
 - Vietnamese
 - Welsh

## Usage

In your Eloquent model, add the `EloquentDate` trait:

```php
<?php

namespace App;

use Illuminate\Database\Eloquent\Model;
use Seiler\EloquentDate\EloquentDate;

class Post extends Model
{
    use EloquentDate;

    /**
     * The attributes that should be mutated to dates.
     *
     * @var array
     */
    protected $dates = [
        'created_at',
        'updated_at',
        'published_at',
    ];
}
```

Now, any attribute declared in `$dates` will be converted to `Date` instance instead of `Carbon`:

```php
\Jenssegers\Date\Date::setLocale('fr');

$post = Post::find(1);

echo $post->published_at->format('l j F Y H:i:s'); // samedi 19 mars 2016 21:58:16
```

To learn all you can do with `Date`, please refer to its own [documentation](https://github.com/jenssegers/date#usage).

## To Do

Tests...

## Contributing

Please see [CONTRIBUTING](CONTRIBUTING.md) for details.

## Security

If you discover any security related issues, please email frederic@seiler.io instead of using the issue tracker.

## Credits

- [Frederic Seiler](https://github.com/fredericseiler) for the trait
- [Jens Segers](https://github.com/jenssegers/date) for the Date library
- [All Contributors](../../contributors)

## License

The MIT License (MIT). Please see [License File](LICENSE.md) for more information.

[ico-version]: https://img.shields.io/packagist/v/seiler/eloquent-date.svg?style=flat-square
[ico-license]: https://img.shields.io/packagist/l/seiler/eloquent-date.svg?style=flat-square
