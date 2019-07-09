# SCSS Material Colors

Easily implement Material Colors in the color scheme of your choice.

<!-- TOC -->
- [SCSS Material Colors](#SCSS-Material-Colors)
  - [Example Preview in VSCode](#Example-Preview-in-VSCode)
  - [Usage](#Usage)
    - [Option A &mdash; Single File, All Colors](#Option-A-mdash-Single-File-All-Colors)
    - [Option B &mdash; Using Separate Color Files](#Option-B-mdash-Using-Separate-Color-Files)
    - [Example: Include All Colors from Sub-Folder](#Example-Include-All-Colors-from-Sub-Folder)
    - [Example: Include Specific Colors from Sub-Folder](#Example-Include-Specific-Colors-from-Sub-Folder)
    - [Option C &mdash; Plain CSS var](#Option-C-mdash-Plain-CSS-var)

---

## Example Preview in VSCode

<img src="https://user-images.githubusercontent.com/145959/52465145-8c6ce880-2b4b-11e9-80a0-7e7e999c58b0.png">

## Usage

These are color sets from the [Material Colors](https://material.io/tools/color/#!/?view.left=0&view.right=0) as
in several variants (in the `_colors.*.scss` files), the default is **HEX**. This setup contains SCSS variables.

### Option A &mdash; Single File, All Colors

The easiest way to use this in scss is with one of the files beginning with `_colors`. The `_colors.scss` is the
default. Yet, freely rename/customize and do as you see fit.

- Copy a `_colors.*` file to your project, and simply `@import 'colors`;
- **&mdash; or &mdash;**
- If you use `_colors.hsla`, I suggest renaming it to `_colors.scss` for simplicity.
- There is no reason to use `_colors, _colors.hsla, _colors.rgba` together, just choose your preference. They are all the same colors.
- **File Differences; This should be obvious.**
- `_colors.scss`:  **ALL colors** are variables in a
  single file; Make sure your bundler omits unused code in this case (For example: `uncss`, mentioned below).
  - `_colors.scss` &mdash; `HEX` **(default)**
  - `_colors.rgba.scss` &mdash; `RGBA`
  - `_colors.hslda.scss` &mdash; `HSLA`
  - `$black` and `$white` are also provided even though they are not official part of Material.

```scss
// Assuming you have _colors.scss:
@import 'colors';
```

### Option B &mdash; Using Separate Color Files

You can choose to use only select colors to avoid more work on for your bundler by importing what you need.

- Copy the `colors` folder to your project.
- Copy a `_sample.*` file to your project, and make adjustments if needed.

- `_sample.all.scss` &mdash; Import **ALL** color files from  `/colors`.
- `_sample.choose.scss` &mdash; Import **ONLY** color files **you choose** from `/colors`.

In your main `styles.scss` simply do an import:

### Example: Include All Colors from Sub-Folder

```scss
// Assuming you have "colors/all.scss" and all files therein, you can add every subfile this way also:
@import 'colors';

body {
  background: $red-50;
  color: $gray-900;
}
```

### Example: Include Specific Colors from Sub-Folder

```scss
// Assuming you have "colors/all.scss" and all files therein, you can add them by what you need only:
@import 'colors/gray';
@import 'colors/red';
@import 'colors/solid'; // Black/White

body {
  background: $red-50;
  color: $gray-900;
}
```

### Option C &mdash; Plain CSS var

If you just want to use the colors in **pure-css** for some reason, included is also:

- These are set in the global `:root` scope.
  - `colors.css`
  - `colors.min.css`

To use **pure-css** Instead of using a SASS variable such as `$gray-500`, use:

```css
`element {
  attribute: val(--gray-500);
  # Or with an optional fall-back if it were not defined
  # attribute: val(--gray-500, '#8e8e8e');
}
```

---

License MIT Open Source

(c) 2019 Jesse Boyer <https://jream.com>
