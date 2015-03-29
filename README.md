Melange
=======

Melange is a powerful yet small CSS framework. It specialised for general usage thus most GUI related styles are
missing. Simply sets basic styles to elements, allows scalability and applies coding standardization for different
type of projects.

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
* Copy the `settings` folder to your projects assets folder.
* The in your `styles scss` file

```
// First import the Settings file
@import "<path-to-settings>/settings";

// After import Melange
@import "<path-to-melange>/lib/melange";

// Then you own Styles
```