# SafeColor
SafeColor generates accessible colors that comply with [WCAG 2.1 success criteria 1.4.3](https://www.w3.org/WAI/WCAG21/quickref/#contrast-minimum) (or any contrast ratio of your choice).
It can be used to:

1. generate a random color that is contrast safe with a given color
2. generate a consistent, contrast safe color for a string

No need to worry about your base color being light/dark or for foreground/background. If the given color is too light to meet your desired contrast ratio, SafeColor will look for a darker color and vise versa.

## A lot of libraries can generate arbitrary colors. Why the fuss?

To improve web accessibility for people with color deficiencies, WCAG 2.1 requires that the visual presentation of text and images of text has a contrast ratio of at least 4.5:1(Level AA) or an enchanced contrast ratio of at least 7:1(Level AAA).

Complying with this principle will improve the accessibility of your web contents.

## Install

`npm install safecolor`

## Usage

`import SafeColor from 'safecolor'`

### Basic

This will assume that the generated color should be contrast safe (>= Level AA: 4.5) with black(`rgb(0, 0, 0)`)

```javascript
  safeColor = new SafeColor()

  safeColor.random()
  // >> rgb(104, 145, 26)
  // contrast ratio = 5.65

  safeColor.random('hello world')
  // >> rgb(196,226,239)
  // contrast ratio = 15.47
```
### With options

```javascript
  safeColor = new SafeColor({
    color: [255, 255, 255],
    contrast: 4.5,
  })

  safeColor.random()
  // >> rgb(32,80,46)
  // contrast ratio = 9.34

  safeColor.random('hello world')
  // >> rgb(20,57,74)
  // contrast ratio = 12.25
```

## Options

**color**

A base color. Should be 8bit RGB value in array `[r, g, b]`

- type: `Array`
- default: `[0, 0, 0]`

**contrast**

The minimum contrast ratio between the base color and the generated color.

- type: `Number`
- default: `4.5`

## Notice
ES6 features: destructing assignment and map are used in this script. You may need polyfills for the script to work properly.

Note: to keep this as simple as possible, the output is a RGB value in string. If any built-in conversions (to HEX, to HSL) will make SafeColor much more convenient for you, please contact me to add the feature or feel free to pull request. Cheers!
