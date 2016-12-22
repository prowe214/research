# Component Libraries

As demonstrated by MaterialUI, Material2, and Bootstrap.

[![GitPitch](https://gitpitch.com/assets/badge.svg)](https://gitpitch.com/prowe214/research/master?grs=github&t=white)

----

#HSLIDE

## Material UI (mui)

[Repo](https://github.com/callemall/material-ui)

#VSLIDE

### mui - A React component library that utilizes:
- JSX
- Base styles
- View encapsulation
- Object-Oriented styles via es6 imports
- State management via javascript events

#VSLIDE

### mui = JSX = React

A Hybrid of HTML and Javascript which allows javascript variable and objects to be passed directly onto an HTML element.

*In ng2, we use the view model and pass controller-bound vars to HTML templates.  Separation of concerns, but same result.*

#VSLIDE

### Creating a `colors` module

**material-ui / src / styles / colors.js**
```
...
export const red700 = '#d32f2f';
export const red800 = '#c62828';
export const red900 = '#b71c1c';
export const redA100 = '#ff8a80';
export const redA200 = '#ff5252';
export const redA400 = '#ff1744';
export const redA700 = '#d50000';
...
export const pink50 = '#fce4ec';
export const pink100 = '#f8bbd0';
export const pink200 = '#f48fb1';
export const pink300 = '#f06292';
...
export const transparent = 'rgba(0, 0, 0, 0)';
export const fullBlack = 'rgba(0, 0, 0, 1)';
export const darkBlack = 'rgba(0, 0, 0, 0.87)';
export const lightBlack = 'rgba(0, 0, 0, 0.54)';
export const minBlack = 'rgba(0, 0, 0, 0.26)';
export const faintBlack = 'rgba(0, 0, 0, 0.12)';

```

#VSLIDE

### Importing Theme

**material-ui / src / styles / getMuiTheme.js**
```
import typography from './typography';

appBar: {
      color: palette.primary1Color,
      textColor: palette.alternateTextColor,
      height: spacing.desktopKeylineIncrement,
      titleFontWeight: typography.fontWeightNormal,
      padding: spacing.desktopGutter,
    },
    avatar: {
      color: palette.canvasColor,
      backgroundColor: emphasize(palette.canvasColor, 0.26),
    },
```

#VSLIDE

### The Theme's palette

**This is where the colors can be configured by a user**

**material-ui/src/styles/baseThemes/lightBaseTheme.js**
```
import {
  red500, grey400, grey500, grey600, grey700,
  transparent, lightWhite, white, darkWhite, lightBlack, black,
} from './colors';

palette: {
    primary1Color: cyan500,
    primary2Color: cyan700,
    primary3Color: grey400,
    accent1Color: pinkA200,
    accent2Color: grey100,
    accent3Color: grey500,
    textColor: darkBlack,
    secondaryTextColor: fade(darkBlack, 0.54),
    alternateTextColor: white,
    canvasColor: white,
    borderColor: grey300,
    disabledColor: fade(darkBlack, 0.3),
    pickerHeaderColor: cyan500,
    clockCircleColor: fade(darkBlack, 0.07),
    shadowColor: fullBlack,
  },
```

#VSLIDE

### Default Base Styles

**material-ui/src/styles/baseThemes/lightBaseTheme.js**
```
/**
*  Light Theme is the default theme used in material-ui. It is guaranteed to
*  have all theme variables needed for every component. Variables not defined
*  in a custom theme will default to these values.
*/
```

#HSLIDE

## Material2

MaterialUI for Angular 2, as used by the Angular team.
[Repo](https://github.com/angular/material2)

*Currently in Alpha*

#VSLIDE

### SCSS, not JS

Material2 passes values through global `scss` variables.

```
@import 'button-base';

[md-button], [md-icon-button] {
  @extend %md-button-base;
  ...
}
[md-icon-button] {
  padding: 0;

  // Reset the min-width from the button base.
  min-width: 0;

  width: $md-icon-button-size;
  height: $md-icon-button-size;

  flex-shrink: 0;

  line-height: $md-icon-button-size;
  border-radius: $md-icon-button-border-radius;

  i, md-icon {
    line-height: $md-icon-button-line-height;
  }
}
```

#VSLIDE

### Centralized imports

Components are imported centrally through [index.ts](https://github.com/angular/material2/blob/master/src/lib/index.ts)

```
export * from './core';
export * from './module';

export * from './button/index';
export * from './button-toggle/index';
export * from './card/index';
export * from './chips/index';
export * from './checkbox/index';
export * from './dialog/index';
export * from './grid-list/index';
export * from './icon/index';
export * from './input/index';
```

#VSLIDE

### Base colors

Base color palette themes are created on object vars, passed in like `$md-light-theme-foreground.disabled-text`

```
// Foreground palette for light themes.
$md-light-theme-foreground: (
  base:            black,
  divider:         rgba(black, 0.12),
  dividers:        rgba(black, 0.12),
  disabled:        rgba(black, 0.38),
  disabled-button: rgba(black, 0.38),
  disabled-text:   rgba(black, 0.38),
  hint-text:       rgba(black, 0.38),
  secondary-text:  rgba(black, 0.54),
  icon:            rgba(black, 0.54),
  icons:           rgba(black, 0.54),
  text:            rgba(black, 0.87)
);
```

#VSLIDE

### Custom Themes

User overrides styles with a single theme file.  [Material2 Docs on Custom Theme](https://github.com/angular/material2/blob/master/guides/theming.md#defining-a-custom-theme)

#VSLIDE

### Multiple themes

For doing things like custom skins, you can extend the previous example to define a second (or third or fourth) theme that is gated by some selector. For example, we could append the following to the example above to define a secondary dark theme:

```
.unicorn-dark-theme {
  $dark-primary: md-palette($md-blue-grey);
  $dark-accent:  md-palette($md-amber, A200, A100, A400);
  $dark-warn:    md-palette($md-deep-orange);

  $dark-theme: md-dark-theme($dark-primary, $dark-accent, $dark-warn);

  @include angular-material-theme($dark-theme);
}
```

With this, any element inside of a parent with the `unicorn-dark-theme` class will use this dark theme
