# Melange Change Log
## Version 0.6.1
- Fix: Missing "disabled" styles in input elements

## Version 0.6.0
- New: Field radius settings added for field styles. Use `$base-field-border-radius` variable to set.
- New: woff2 font type support settings added for `font-face` mixins.
- New: Border Radius setting added for button styles. Use `$base-button-border-radius` variable to set one. Default is `null`
- New: `button-colors` mixin added for button styles. 
- New: Breakpoints settings added. `$base-widescreen`, `$base-desktop`, `$base-tablet`, `$base-tablet-landscape`, `$base-tablet-portrait` and `$base-phone` variables added both to default variables and settings.
- New: `.mobile-hidden`, `.mobile-visible` auxiliary classes added.
- Change: Predefined font-size definitions from _normalize.css_ removed
- Fix: `text-decoration: underline` problem for anchor buttons resolved.