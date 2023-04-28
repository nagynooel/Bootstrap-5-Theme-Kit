# Bootstrap 5 Theme Kit

This is a simple way to create a basic custom theme for bootstrap.
This project was created with the help of 2 youtube videos:
* [Alexander Rechsteiner - Customize Bootstrap: How to build your own themes for Bootstrap 4](https://www.youtube.com/watch?v=Gi5ffoE3mPc&t=180s)
* [Pixel Rocket - Change Bootstrap's colors](https://www.youtube.com/watch?v=au5ccstcbnc&t=43s)

**These videos are not to replace the guide below and they are not tutorials specific to this repo!**

The theming-kit.html file is an upgraded version of [Alexander Rechsteiner's](https://github.com/HackerThemes/theme-kit), it now includes forms and bootstrap 5 specific form elements/functionalites like floating labels and form validation.

## Prerequisites

* Windows, MacOs or Linux operating system
* Node package manager ([npm](https://nodejs.org/en))
* Some sort of Sass compiler, I recomend using the VS code extension [Live Sass Compiler](https://marketplace.visualstudio.com/items?itemName=glenn2223.live-sass) or [gulp](https://gulpjs.com/). This guide will focus on the extension!

## Usage

1. Clone this repository
2. Run `npm install`
3. Configure your Sass compiler:
    1. Set format to "compressed"
    2. Set extension name to ".min.css"
    3. Set save path to "/css"
    
    **See below for VS code Live Sass Compiler exstension configuration**
4. Start your compiler
5. Write your custom variables into `./sass/_variables.scss` and your map amends into `./sass/_map-amends.scss` file
6. When done customizing your Theme, just copy the `./css/main.min.css` file into your projects directory and link it as usual

## VS Code Live Compiler setup

1. Open VS Code settings (Bottom Left corner)
2. Search for "live sass"
3. Click on "Edit in settings.json"
4. Search for "liveSassCompile.settings.formats"
5. Edit it as follows:
```JSON
    {
        "format": "compressed",
        "extensionName": ".min.css",
        "savePath": "/css",
        "savePathReplacementPairs": null
    }
```

## _variables.scss file

In this file you can overwrite all of the bootstrap sass variables and even create new ones.
You can find all variables in `./node_modules/bootstrap/scss/_variables.scss`

**Note that this file is imported before the default bootstrap variables file, therefore those variables can not be used!**

Some example variables:
```SCSS
// Change basic colors
$primary: #FFC529;
$secondary: #FE724C;
$dark: #272D2F;
$light: #D7D7D7;

$body-bg: #d3e9eb;
$body-color: #151417;

// Enable shadows and gradients on all kinds of objects like buttons
$enable-shadows: true;
$enable-gradients: true;

// Enable rounded edges and set the radius
$enable-rounded: true;
$border-radius: 15px;
```

## _map-amends.scss file

Here you can amend any of the maps that are included in bootstrap's _variables.scss file. If you would create the maps in your variables file, they would overwrite the bootstrap one.

**This file is imported after the default bootstrap variables file, therefore those variables CAN also be used.**

This is mainly used to create new colors. The basic code for that is included in the file. You just need to add a key-value pair into the $custom-colors map.

Here is an example:
```SCSS
$custom-colors: (
    "mycolor": #9A92C2,
    "error": $danger
);

$theme-colors: map-merge($theme-colors, $custom-colors);
```

## Using different bootstrap versions

**This project includes Bootstrap 5.2.3**
You can use older or newer versions easily. Just run `npm install bootstrap@version --save `, where version is the specific version we want or u can use `npm update bootstrap` to get the latest version.

If you are using Bootstrap 4 or older some features in the html file may not work, for example the floating label inputs!

**Don't forget to recompile the scss file after installing a new version!**

## Copyright and License

Code and documentation copyright 2023 [Noel Nagy](https://github.com/nagynooel)

Code released under the [MIT License](https://opensource.org/license/mit/).