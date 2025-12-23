# Customization

## Current Limitations

The package currently does **not** provide configuration options. All styling is applied globally through the registered CSS asset.

## Overriding Styles

If you need custom scrollbar styles, you can override them in your application CSS.

### In Your Custom Theme

If you have a custom Filament theme, add your overrides after Filament's styles:

```css
/* resources/css/filament/theme.css */

@import '../../../../vendor/filament/filament/resources/css/theme.css';

/* Override scrollbar width */
::-webkit-scrollbar {
    height: 8px;
    width: 8px;
}

/* Custom colors */
::-webkit-scrollbar-thumb {
    background: #3b82f6;
}

::-webkit-scrollbar-thumb:hover {
    background: #2563eb;
}
```

### Via Custom CSS in Panel Provider

You can inject custom CSS through your panel provider:

```php
use Filament\Panel;

public function panel(Panel $panel): Panel
{
    return $panel
        ->id('admin')
        // ... other configuration
        ->renderHook(
            'panels::head.end',
            fn () => view('filament.custom-scrollbar-styles')
        );
}
```

Create the view file:

```blade
{{-- resources/views/filament/custom-scrollbar-styles.blade.php --}}
<style>
    ::-webkit-scrollbar {
        width: 8px;
        height: 8px;
    }
    
    ::-webkit-scrollbar-thumb {
        background: {{ filament()->getColors()['primary'][600] }};
    }
</style>
```

## Color Customization

The current colors used are:

### Light Mode
- Track: `#e5e7eb` (gray-200)
- Thumb: `#d1d5db` (gray-300)
- Thumb hover: `#c9cbcd` (custom gray)

### Dark Mode
- Track: `#101215` (custom dark)
- Thumb: `#1f2126` (custom dark gray)
- Thumb hover: `#1a1d21` (custom darker gray)

## Per-Component Styling

To style scrollbars for specific components, use CSS selectors:

```css
/* Only for tables */
.fi-ta-table ::-webkit-scrollbar {
    width: 6px;
}

/* Only for modals */
.fi-modal ::-webkit-scrollbar-thumb {
    background: #9333ea;
}

/* Only for specific panel */
#admin ::-webkit-scrollbar {
    width: 10px;
}
```

## Disabling the Package

If you want to disable the slim scrollbar styling:

1. Remove the package:
```bash
composer remove akira/filament-slim-scrollbar
```

Or

2. Override with default browser styles:
```css
::-webkit-scrollbar {
    width: auto;
    height: auto;
}

::-webkit-scrollbar-track {
    background: transparent;
}

::-webkit-scrollbar-thumb {
    background: auto;
}
```

## Future Configuration

In future versions, the package may provide:
- Configuration file for dimensions and colors
- Per-panel configuration
- Theme-based color schemes
- Artisan commands for publishing config

See the [Roadmap](00-roadmap.md) for planned features.

**Previous:** [How It Works](02-how-it-works.md) | **Next:** [Browser Support](04-browser-support.md)
