# Browser Support

## Webkit Browsers (Full Support)

The package uses `::-webkit-scrollbar` pseudo-elements, which are fully supported in:

### Chrome/Chromium
- All recent versions
- Desktop and mobile
- Full scrollbar customization support

### Safari
- Safari 14+
- iOS Safari 14+
- Full scrollbar customization support

### Edge (Chromium)
- Edge 79+ (Chromium-based)
- Full scrollbar customization support
- Legacy Edge (EdgeHTML) not supported

### Opera
- Opera 15+ (Chromium-based)
- Full scrollbar customization support

### Brave
- All recent versions
- Full scrollbar customization support

## Non-Webkit Browsers

### Firefox
- Does **not** support `::-webkit-scrollbar`
- Uses default Firefox scrollbar styling
- Firefox has its own scrollbar customization (not implemented)

### Other Browsers
- Any browser not based on Webkit/Blink
- Will use their default scrollbar styling
- Styles are safely ignored (no errors)

## Progressive Enhancement

This package follows the progressive enhancement principle:

1. **Webkit browsers** get slim, styled scrollbars
2. **Other browsers** use their default scrollbars
3. **No browsers** experience errors or broken functionality

The website remains fully functional regardless of browser support.

## Testing Across Browsers

When testing your Filament application:

### Expected Behavior in Chrome/Safari/Edge
- 4px slim scrollbars
- Custom colors (light/dark mode)
- Hover effects

### Expected Behavior in Firefox
- Default Firefox scrollbars
- No custom styling
- Full functionality maintained

## Mobile Browser Support

### iOS Safari
- Scrollbars are typically hidden by default
- Custom styles apply when scrollbars are visible
- Does not affect touch scrolling behavior

### Chrome Mobile (Android)
- Limited scrollbar visibility
- Custom styles apply when visible
- Does not affect touch scrolling

## Future Browser Support

### Firefox Scrollbar Styling

Firefox supports scrollbar styling through different properties:

```css
/* Firefox scrollbar styling (not currently implemented) */
* {
    scrollbar-width: thin;
    scrollbar-color: #d1d5db #e5e7eb;
}
```

This may be added in a future version. See the [Roadmap](00-roadmap.md).

## CSS Standards

The `::-webkit-scrollbar` pseudo-elements are **non-standard**:
- Not part of official CSS specification
- No W3C standard equivalent exists yet
- Webkit vendors maintain implementation

## Checking Browser Compatibility

You can detect webkit scrollbar support with JavaScript:

```javascript
const supportsWebkitScrollbar = CSS.supports(
    'selector(::-webkit-scrollbar)'
);
```

However, this package does not require any JavaScript detection since CSS gracefully handles unsupported properties.

## Accessibility

The scrollbar styling:
- Does not affect scrolling functionality
- Maintains browser's native scroll behavior
- Does not interfere with keyboard navigation
- Does not affect screen readers

**Previous:** [Customization](03-customization.md) | **Next:** [Troubleshooting](05-troubleshooting.md)
