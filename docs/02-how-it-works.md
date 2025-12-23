# How It Works

## Architecture Overview

Filament Slim Scrollbar is a CSS-only package that modifies the appearance of scrollbars in Filament panels through webkit pseudo-elements.

## Service Provider

The package uses a single service provider: `FilamentSlimScrollbarServiceProvider`

```php
namespace Akira\FilamentSlimScrollbar;

use Filament\Support\Assets\Css;
use Filament\Support\Facades\FilamentAsset;
use Spatie\LaravelPackageTools\Package;
use Spatie\LaravelPackageTools\PackageServiceProvider;

class FilamentSlimScrollbarServiceProvider extends PackageServiceProvider
{
    public static string $name = 'filament-slim-scrollbar';

    public function configurePackage(Package $package): void
    {
        $package->name(static::$name)
            ->hasAssets();

        FilamentAsset::register(
            assets: [
                Css::make(static::$name, __DIR__ . '/../resources/dist/app.css'),
            ],
            package: 'akira/filament-slim-scrollbar'
        );
    }
}
```

## CSS Asset Registration

The service provider registers a CSS file with Filament's asset system using `FilamentAsset::register()`. This ensures the styles are loaded on all Filament pages.

### Asset Path
- Source: `resources/dist/app.css`
- Package: `akira/filament-slim-scrollbar`
- Type: CSS

## CSS Implementation

The scrollbar styling is achieved through webkit pseudo-elements:

### Scrollbar Dimensions
```css
::-webkit-scrollbar {
    height: 4px;
    width: 4px
}
```

### Light Mode Styling
```css
::-webkit-scrollbar-track {
    background: #e5e7eb
}

::-webkit-scrollbar-thumb {
    background: #d1d5db
}

::-webkit-scrollbar-thumb:hover {
    background: #c9cbcd
}
```

### Dark Mode Styling
```css
.dark ::-webkit-scrollbar-track {
    background: #101215
}

.dark ::-webkit-scrollbar-thumb {
    background: #1f2126
}

.dark ::-webkit-scrollbar-thumb:hover {
    background: #1a1d21
}
```

## Filament Theme Integration

The CSS imports Filament's base theme:

```css
@import '../../vendor/filament/filament/resources/css/theme.css';
```

This ensures compatibility with Filament's dark mode switching and theme system.

## Loading Sequence

1. Laravel boots and discovers the service provider
2. Service provider registers with Filament
3. Filament asset system loads the CSS file
4. CSS is included in all Filament panel pages
5. Webkit browsers apply the scrollbar styles

## No JavaScript Required

This package uses pure CSS with no JavaScript dependencies. This means:
- Zero performance impact
- No DOM manipulation
- No event listeners
- Instant rendering
- Works with SSR

## Browser Specificity

The `::-webkit-scrollbar` pseudo-elements are vendor-prefixed and only work in webkit-based browsers. Other browsers ignore these styles and use their default scrollbars.

**Previous:** [Installation](01-installation.md) | **Next:** [Customization](03-customization.md)
