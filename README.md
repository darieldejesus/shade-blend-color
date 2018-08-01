Shade Blend Color
============

A small script that will take a HEX or RGB web color, shade it darker or lighter, or blend it with a second color, and can also pass it right thru but convert from Hex to RGB (Hex2RGB) or RGB to Hex (RGB2Hex). All without you even knowing what color format you are using.

## Disclaimer

This script was developed by Pimp Trizkit. I just want to make it available through ***npm***. 
You can see his StackOverflow profile [Pimp Trizkit] and for more information, visit: <a href="https://stackoverflow.com/a/13542669/3130385" target="_blank">Programmatically Lighten or Darken a hex color (or rgb, and blend colors)</a>.

## Installation

```bash
npm install shade-blend-color
```

## Demo

In the meantime, you can test the scripts through the official demo by the author of this script:
[jsFiddle with pSBC]


## Usages

To see its features and params specifications, please visit: [The official wiki]

```js
import pSBC from 'shade-blend-color';

let color1 = "rgb(20,60,200)";
let color2 = "rgba(20,60,200,0.67423)";
let color3 = "#67DAF0";
let color4 = "#5567DAF0";
let color5 = "#F3A";
let color6 = "#F3A9";
let color7 = "rgb(200,60,20)";
let color8 = "rgba(200,60,20,0.98631)";
let color;

color = pSBC ( 0.42, color1 ); // rgb(20,60,200) + [42% Lighter] => rgb(119,142,223)
color = pSBC ( -0.4, color5 ); // #F3A + [40% Darker] => #991f66
color = pSBC ( 0.42, color8 ); // rgba(200,60,20,0.98631) + [42% Lighter] => rgba(223,142,119,0.98631)

// Shade with Conversion (use "c" as your "to" color)
color = pSBC ( 0.42, color2, "c" ); // rgba(20,60,200,0.67423) + [42% Lighter] + [Convert] => #778edfac

// RGB2Hex & Hex2RGB Conversion Only (set percentage to zero)
color = pSBC ( 0, color6, "c" ); // #F3A9 + [Convert] => rgba(255,51,170,0.6)

// Blending
color = pSBC ( -0.5, color2, color8 ); // rgba(20,60,200,0.67423) + rgba(200,60,20,0.98631) + [50% Blend] => rgba(110,60,110,0.8303)
color = pSBC ( 0.7, color2, color7 ); // rgba(20,60,200,0.67423) + rgb(200,60,20) + [70% Blend] => rgba(146,60,74,0.67423)
color = pSBC ( 0.25, color3, color7 ); // #67DAF0 + rgb(200,60,20) + [25% Blend] => rgb(127,179,185)
color = pSBC ( 0.75, color7, color3 ); // rgb(200,60,20) + #67DAF0 + [75% Blend] => #7fb3b9

// Error Checking
color = pSBC ( 0.42, "#FFBAA" ); // #FFBAA + [42% Lighter] => null  (Invalid Input Color)
color = pSBC ( 42, color1, color5 ); // rgb(20,60,200) + #F3A + [4200% Blend] => null  (Invalid Percentage Range)
color = pSBC ( 0.42, {} ); // [object Object] + [42% Lighter] => null  (Strings Only for Color)
color = pSBC ( "42", color1 ); // rgb(20,60,200) + ["42"] => null  (Numbers Only for Percentage)
color = pSBC ( 0.42, "salt" ); // salt + [42% Lighter] => null  (A Little Salt is No Good...)

// Error Check Fails (Some Errors are not Caught)
color = pSBC ( 0.42, "#salt" ); // #salt + [42% Lighter] => #6b6b6b00  (...and a Pound of Salt is Jibberish)

// Ripping
color = pSBCr ( color4 ); // #5567DAF0 + [Rip] => [object Object] => {'0':85,'1':103,'2':218,'3':0.9412}
```

[Pimp Trizkit]: https://stackoverflow.com/users/693927/pimp-trizkit
[jsFiddle with pSBC]: https://jsfiddle.net/PimpTrizkit/a7ac0qvp/
[The official wiki]: https://github.com/PimpTrizkit/PJs/wiki/12.-Shade,-Blend-and-Convert-a-Web-Color-(pSBC.js)
