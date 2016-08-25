# Melange Change Log
## Version 0.7.0
- NEW: sass-lint added for better standardization
- NEW: `%melange-*` placeholders added for most of the melange default classes.
- NEW: `$predefined-classes` variable added to control if Melange classes will stay as placeholders for the project `@extend`s or css outputs. To prevent major breakdowns, default value set to `true`
- CHANGE: Normalize version updated to `4.1.1`
- CHANGE: Underscored variable names changed to their dashed versions.
- FIX: Coding style revised according to sass-lint configurations.


## Version 0.6.1
- FIX: Missing "disabled" styles in input elements

## Version 0.6.0
- NEW: Field radius settings added for field styles. Use `$base-field-border-radius` variable to set.
- NEW: woff2 font type support settings added for `font-face` mixins.
- NEW: Border Radius setting added for button styles. Use `$base-button-border-radius` variable to set one. Default is `null`
- NEW: `button-colors` mixin added for button styles. 
- NEW: Breakpoints settings added. `$base-widescreen`, `$base-desktop`, `$base-tablet`, `$base-tablet-landscape`, `$base-tablet-portrait` and `$base-phone` variables added both to default variables and settings.
- NEW: `.mobile-hidden`, `.mobile-visible` auxiliary classes added.
- CHANGE: Predefined font-size definitions from _normalize.css_ removed
- FIX: `text-decoration: underline` problem for anchor buttons resolved.