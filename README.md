# Filament Slim Scrollbar

[![Latest Version on Packagist](https://img.shields.io/packagist/v/akira/filament-slim-scrollbar.svg?style=flat-square)](https://packagist.org/packages/akira/filament-slim-scrollbar)
[![GitHub Tests Action Status](https://img.shields.io/github/actions/workflow/status/akira/filament-slim-scrollbar/tests.yml?branch=1.x&label=tests&style=flat-square)](https://github.com/akira/filament-slim-scrollbar/actions?query=workflow%3Atests+branch%3A1.x)
[![Total Downloads](https://img.shields.io/packagist/dt/akira/filament-slim-scrollbar.svg?style=flat-square)](https://packagist.org/packages/akira/filament-slim-scrollbar)

A lightweight Filament package that provides elegant, slim scrollbars for all Filament panels. Pure CSS implementation with automatic light/dark mode support and zero configuration required.

## Features

-  **Slim Design**: 4px width/height scrollbars
-  **Dark Mode**: Automatic light/dark theme support
-  **Zero Config**: Works out of the box
-  **Performance**: Pure CSS, no JavaScript
-  **Filament Native**: Integrates seamlessly with Filament's asset system
-  **Customizable**: Easy to override with your own styles

## Requirements

- PHP 8.1, 8.2, 8.3, 8.4, or 8.5
- Laravel 10.x, 11.x, or 12.x
- Filament 3.x or 4.x

## Installation

Install the package via Composer:

```bash
composer require akira/filament-slim-scrollbar
```

That's it! The package automatically registers itself and applies slim scrollbars to all Filament panels.

## Browser Support

Full support in webkit-based browsers:
- ✅ Chrome/Chromium
- ✅ Safari
- ✅ Edge (Chromium)
- ✅ Opera
- ✅ Brave
- ⚠️ Firefox (uses default scrollbars - webkit styling not supported)

## Customization

The package works with zero configuration, but you can customize the scrollbar styles by overriding the CSS in your custom theme:

```css
/* resources/css/filament/theme.css */

::-webkit-scrollbar {
    width: 8px;  /* Change width */
    height: 8px;
}

::-webkit-scrollbar-thumb {
    background: #3b82f6;  /* Custom color */
}
```

For more customization options, see the [full documentation](https://packages.akira-io.com/packages/filament-slim-scrollbar).

## Documentation

Complete documentation is available at [https://packages.akira-io.com/packages/filament-slim-scrollbar](https://packages.akira-io.com/packages/filament-slim-scrollbar)

- [Installation Guide](docs/01-installation.md)
- [How It Works](docs/02-how-it-works.md)
- [Customization](docs/03-customization.md)
- [Browser Support](docs/04-browser-support.md)
- [Troubleshooting](docs/05-troubleshooting.md)
- [Roadmap](docs/00-roadmap.md)

## Testing

```bash
composer test
```

## Changelog

Please see [CHANGELOG](CHANGELOG.md) for more information on what has changed recently.

## Contributing

Please see [CONTRIBUTING](.github/CONTRIBUTING.md) for details.

## Security Vulnerabilities

Please review [our security policy](.github/SECURITY.md) on how to report security vulnerabilities.

## Credits

- [kid](https://github.com/kidiatoliny)
- [All Contributors](../../contributors)

## License

The MIT License (MIT). Please see [License File](LICENSE.md) for more information.
