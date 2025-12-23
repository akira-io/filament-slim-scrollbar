# Installation

## Requirements

- PHP 8.1, 8.2, 8.3, 8.4, or 8.5
- Laravel 10.x, 11.x, or 12.x
- Filament 3.x or 4.x

## Installation Steps

Install the package via Composer:

```bash
composer require akira/filament-slim-scrollbar
```

The package will automatically register itself through Laravel's package discovery.

## What Gets Installed

The package registers:

1. **Service Provider**: `Akira\FilamentSlimScrollbar\FilamentSlimScrollbarServiceProvider`
2. **CSS Asset**: Registered with Filament's asset system
3. **Auto-discovery**: Automatically loaded by Filament

## No Additional Configuration Required

The package works out of the box. Once installed, all Filament panels will automatically use the slim scrollbar styles.

## Verification

After installation, visit any Filament panel in your application. You should see:

- Scrollbars with 4px width/height
- Light gray scrollbar in light mode
- Dark scrollbar in dark mode
- Smooth hover effects

## Troubleshooting

### Scrollbar Not Appearing

If the scrollbar styles are not applied:

1. Clear your application cache:
```bash
php artisan optimize:clear
```

2. Rebuild your assets if you have custom theme:
```bash
npm run build
```

3. Verify the package is loaded:
```bash
php artisan package:discover
```

### Browser Compatibility

The scrollbar styling uses `::-webkit-scrollbar` pseudo-elements, which work in:
- Chrome/Chromium
- Edge (Chromium-based)
- Safari
- Opera

Firefox and other browsers will use their default scrollbar styling.

**Previous:** [Roadmap](00-roadmap.md) | **Next:** [How It Works](02-how-it-works.md)
