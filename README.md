# Melange

Melange is a powerful yet small CSS framework. It specialised for general usage thus most GUI related styles are
missing. Simply sets basic styles to elements, allows scalability and applies coding standardization for different
type of projects. You can find the usage at [Melange Sample](https://github.com/bcinarli/melange-sample) repo

## Installation
Melange can directly install your project by copying the contents of lib folder to your assets, or you can install it as [npm](https://www.npmjs.org/) or [bower](http://bower.io) packages. Just run,
with npm

```
npm install melange
```

or with bower

```
bower install melange
```

After copying the files, 
* Copy the `settings` folder to your projects' assets folder.
* Then in your styles file

```SCSS
// First import the Settings file
@import "<path-to-settings>/settings";

// After import Melange
@import "<path-to-melange>/lib/melange";

// Then your own Styles

// After you styles, add Melange Auxiliary components
@import "<path-to-melange>/lib/melange/auxiliary/auxiliary"
```
