Changelog
=========

## version 2.4.0 (2020-07-18)

### Added: {docsify-ignore}

+ New **Radial** visualization - see [`radial`](README.md#radial-boolean) and [`spinSpeed`](README.md#spinspeed-number) properties and try them in the [demos](https://audiomotion.dev/demo)!
+ [`showScaleY`](README.md#showscaley-boolean) property for displaying the level (dB) scale on the analyzer's vertical axis;
+ [`energy`](README.md#energy-number-read-only) and [`peakEnergy`](README.md#peakenergy-number-read-only) read-only properties;
+ [Known issues](README.md#known-issues) section added to the documentation.

### Changed: {docsify-ignore}

+ [`setOptions()`](README.md#setoptions-options-) called with no argument now **resets all configuration options to their default values** (it used to raise an error);
+ The LED effect code has been refactored to improve appearance and compatibility with other (future) effects;
+ "Unlit" LEDs are no longer displayed in **overlay mode** - see the notice in [`showBgColor`](README.md#showbgcolor-boolean) documentation;
+ Canvas `fillStyle` and `strokeStyle` properties are now set with the current gradient before calling the [`onCanvasDraw`](README.md#oncanvasdraw-function) callback function;
+ Updated all [demos](https://audiomotion.dev/demo) with more straightforward access to configuration options.


## version 2.3.0 (2020-06-08)

### Added: {docsify-ignore}

+ [`binToFreq()`](README.md#bintofreq-bin-) and [`freqToBin()`](README.md#freqtobin-frequency-rounding-) methods;
+ [`reflexBright`](README.md#reflexbright-number) property, which allows to adjust the brightness of the reflected image.

### Changed: {docsify-ignore}

+ Reverted the change to `reflexAlpha` introduced in [v2.2.1](https://github.com/hvianna/audioMotion-analyzer/releases/tag/2.2.1)
+ Removed the forced black layer off the reflection background.


## version 2.2.1 (2020-05-31)

### Changed: {docsify-ignore}

+ ~~Improved the Reflex effect in [`overlay`](README.md#overlay-boolean) mode - the [`reflexAlpha`](README.md#reflexalpha-number) property is
now used to adjust the opacity of a dark layer applied *over* the reflection area, which prevents undesired transparency of the reflection itself
and creates a consistent effect, whether overlay mode is on or off~~ **(reverted in v2.3.0)**;

+ The package source code has been moved from the `dist` to the `src` folder.

### Fixed: {docsify-ignore}

+ Prevent showing leds below the 0 level, when both reflex and overlay are active.


## version 2.2.0 (2020-05-19)

### Added: {docsify-ignore}

+ New [`overlay`](README.md#overlay-boolean) and [`bgAlpha`](README.md#bgalpha-number) properties allow displaying the analyzer over other contents.
[Check out the new demo!](https://audiomotion.dev/demo/overlay.html)

### Changed: {docsify-ignore}

+ Corrected the documentation for the [`registerGradient()`](README.md#registergradient-name-options-) method, which stated the `bgColor` property was required (it has always been optional).


## version 2.1.0 (2020-04-06)

### Added: {docsify-ignore}

+ Customizable Reflex effect - see [`reflexRatio`](README.md#reflexratio-number) and try it in the [demo](https://audiomotion.dev/demo/fluid.html).


## version 2.0.0 (2020-03-24)

### Added: {docsify-ignore}

+ New [`lineWidth`](README.md#linewidth-number) and [`fillAlpha`](README.md#fillalpha-number) properties for [mode 10](README.md#mode-number) customization, so it can now work as an area graph (default), a line graph or a combination of both;
+ New [`barSpace`](README.md#barspace-number) property for customizable bar spacing in octave bands modes;
+ You can now provide an external AudioContext via `audioCtx` property in the [constructor's `options`](README.md#constructor), allowing you to share the same context among different instances;
+ Custom [error codes](README.md#custom-errors);
+ New [`version`](README.md#version-string-read-only) property;

### Changed: {docsify-ignore}

+ Increased default spacing between bars in octave bands modes - to get the previous look, set [`barSpace`](README.md#barspace-number) to **1**;
+ Improved accuracy when positioning the X-axis scale labels in octave bands modes;
+ Slightly improved vertical usage of canvas when the LED effect is active (removed the black line at the bottom of the screen);
+ Canvas context is now saved before calling the user callback function and restored afterwards, to avoid undesirable changes;
+ Several functions were refactored for improved legibility, memory usage and performance;
+ Improved documentation and demos;

### Fixed: {docsify-ignore}

+ The multi-instance demo should now work on browsers other than Firefox (it now uses a shared audio context);
+ `isFullscreen` property now correctly reads `false` (instead of `undefined`) when the analyzer is not in fullscreen (*potentially breaking change*);
+ Setting one of the callback functions to `undefined` with `setOptions()` now properly unregisters the callback (*potentially breaking change*);

### API breaking changes: {docsify-ignore}

+ `audioCtx`, `analyzer`, `canvas` and `canvasCtx` objects are now read-only (`canvasCtx` properties may be safely modified while inside the callback for `onCanvasDraw`);
+ `frame` and `time` properties are not exposed anymore, as they are intended for internal use only;
+ `registerGradient()` method now enforces the `name` argument being a non-empty `string` (throws an [error](README.md#custom-errors) otherwise);
+ Errors now return a custom object and some error messages have changed - use the new [`code` property](README.md#custom-errors) to identify errors in a reliable way.


## version 1.2.0 (2019-12-19)

+ Improves the look of bars at lower frequencies in octave bands modes (especially 1/12th and 1/24th);
+ Minor tweak to the "Rainbow" gradient to make cyan and blue shades a little more balanced.


## version 1.1.0 (2019-12-08)

+ New **Area fill** visualization mode (`mode: 10`), which uses the same full-frequency data of the *discrete frequencies* mode, but generates a brighter filled shape;
+ New **Luminance Bars** option (`lumiBars: <boolean>`) for octave bands modes, which displays analyzer bars always at full-height, with varying luminance instead.


## version 1.0.1 (2019-10-22)

+ Minor cleanup to optimize npm package size.


## version 1.0.0 (2019-10-07)

+ First stable release.


## version 1.0.0-rc.1 (2019-10-05)

+ Release candidate for v1.0.0
