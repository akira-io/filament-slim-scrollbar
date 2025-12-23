# Troubleshooting

## Styles Not Applied

### Problem
Scrollbar styles are not visible after installing the package.

### Solutions

1. **Clear Laravel cache**
```bash
php artisan optimize:clear
```

2. **Verify package discovery**
```bash
php artisan package:discover
```

You should see `akira/filament-slim-scrollbar` in the discovered packages list.

3. **Check browser compatibility**
Open your application in Chrome or Safari (webkit-based browsers). Firefox does not support webkit scrollbar styling.

4. **Inspect CSS loading**
Open browser DevTools → Network tab → Filter by CSS. Look for `filament-slim-scrollbar` CSS file.

5. **Rebuild assets (if using custom theme)**
```bash
npm run build
```

## Dark Mode Not Working

### Problem
Dark mode scrollbar colors not applied when switching themes.

### Solutions

1. **Verify Filament dark mode**
Check that Filament's dark mode is properly configured in your panel:

```php
use Filament\Panel;

public function panel(Panel $panel): Panel
{
    return $panel
        ->darkMode(); // Enable dark mode support
}
```

2. **Check CSS selector specificity**
If you have custom CSS, ensure it doesn't override the dark mode styles:

```css
/* This would prevent dark mode from working */
::-webkit-scrollbar-track {
    background: #e5e7eb !important; /* Remove !important */
}
```

3. **Browser cache**
Hard refresh your browser:
- Chrome/Edge: `Ctrl+Shift+R` (Windows) or `Cmd+Shift+R` (Mac)
- Safari: `Cmd+Option+R`

## Scrollbar Too Small

### Problem
4px scrollbar is too small for your use case.

### Solution

Override the width in your custom CSS:

```css
::-webkit-scrollbar {
    width: 8px;
    height: 8px;
}
```

See [Customization](03-customization.md) for more details.

## Scrollbar Shows in Firefox

### Problem
You're seeing default scrollbars in Firefox instead of slim ones.

### Explanation

This is **expected behavior**. Firefox does not support `::-webkit-scrollbar` pseudo-elements. See [Browser Support](04-browser-support.md) for more information.

### Alternative

You can add Firefox-specific scrollbar styling:

```css
/* Add to your custom CSS */
* {
    scrollbar-width: thin;
    scrollbar-color: #d1d5db #e5e7eb;
}

.dark * {
    scrollbar-color: #1f2126 #101215;
}
```

## Conflicts with Custom Themes

### Problem
Your custom theme scrollbar styles conflict with this package.

### Solution

Override the package styles in your theme CSS by placing your rules after the import:

```css
/* resources/css/filament/theme.css */
@import '../../../../vendor/filament/filament/resources/css/theme.css';

/* Your custom scrollbar styles here */
::-webkit-scrollbar {
    /* Your overrides */
}
```

CSS cascade will give priority to rules defined later.

## Package Not Found After Installation

### Problem
Composer can't find the package or shows 404 error.

### Solutions

1. **Verify package name**
```bash
composer require akira/filament-slim-scrollbar
```

2. **Check Composer repositories**
Ensure you have Packagist as a repository in `composer.json`:

```json
{
    "repositories": [
        {
            "type": "composer",
            "url": "https://packagist.org"
        }
    ]
}
```

3. **Update Composer**
```bash
composer self-update
composer update
```

## Performance Issues

### Problem
Concerned about CSS performance impact.

### Explanation

This package has **zero performance impact**:
- Pure CSS (no JavaScript)
- Less than 30 lines of CSS
- No DOM manipulation
- No event listeners
- Loaded once with Filament assets

The package cannot cause performance issues.

## Asset Publishing

### Problem
Need to modify the CSS file directly.

### Current Limitation

The package does not support asset publishing yet. To customize, use CSS overrides as described in [Customization](03-customization.md).

### Future Support

Asset publishing may be added in a future version. See [Roadmap](00-roadmap.md).

## Composer Update Conflicts

### Problem
Getting dependency conflicts during `composer update`.

### Solutions

1. **Check PHP version**
Package requires PHP 8.1 or higher:
```bash
php -v
```

2. **Check Laravel version**
Package supports Laravel 10.x, 11.x, and 12.x:
```bash
php artisan --version
```

3. **Check Filament version**
Package supports Filament 3.x and 4.x:
```bash
composer show filament/filament
```

4. **Update dependencies**
```bash
composer update --with-all-dependencies
```

## Still Having Issues?

If none of these solutions work:

1. Check [GitHub Issues](https://github.com/akira/filament-slim-scrollbar/issues)
2. Search for existing similar issues
3. Create a new issue with:
   - PHP version
   - Laravel version
   - Filament version
   - Browser and version
   - Steps to reproduce

**Previous:** [Browser Support](04-browser-support.md)
