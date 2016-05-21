# Responseless

Responseless is a set of LESS mixins for working with responsive layouts.

Responseless was created to deal with a common scenario web developers face: being handed a pair of
designs for a website for mobile and desktop layouts. Often we get little information on the gulf
between these two extremes. Just as often the "mobile" layout adheres to a single device, and does
not address the enormous variety of devices represented by "Mobile". The range of devices, between
large 30 inch displays and 10 inch netbooks, which might need to support "Desktop" is also often
under appreciated at this stage.

## Getting Started

First, you'll want to install Responseless from NPM.

    npm install responseless

And you'll be able to import it in your project's LESS stylesheets.

    @import (reference) "../../../node_modules/@caktus/responseless/response.less";

Before you use Responseless, you'll need to initialize the mixins by invoking the
`setup-responseless()` mixin, which takes two parameters:

- `max-mobile` The largest size supported for mobile or phone layouts
- `max-page-width` The largest size the main content well for the desktop layout should expand to

Once initialize, all Responseless mixins will become available.

## Layouts

### Small Layout

Up to the `@max-mobile` width we work with the Small Layout.

### Full Layout

Above the `@min-desktop` width we work with the Full Layout.

### Shim Layout

The gap above the `@max-mobile` but below the `@min-desktop` is called the *Shim*. This is the
space between the mobile and desktop mockups we often have to work with.

## Mixins

### `small(rules)`

Define a ruleset that applies only to the Small Layout

### `shim(rules)`

Define a ruleset that applies only to the Shim Layout

### `full(rules)`

Define a ruleset that applies only to the Full Layout

### `not-full(rules)`

Define a ruleset that applies above the Small Layout, to both the Shim and Full Layouts.

### `responsive(defaults, small, full)`

The power-horse mixin of Responseless:

    responsive({
        // Default style properties
        // Applies to all layouts
    }, {
        // Small style properties
        // Applies only to Small Layout
        // Overrides defaults
    }, {
        // Full style properties
        // Applies only to Full Layout
        // Overrides defaults
    });

The third ruleset, for Large Layout styles, can be omitted.

### `shim-interpolate(property, from, to)`

This magical property will help with styles in the gap between Small and Full layouts. The
`shim-interpolate()` mixin defines how a property can scale between the low and high ends of the
Shim. The `from` value will apply just above the largest Small Layout, while the `to` value will
apply just below the smallest Full Layout. Between these two sizes, the values will be
interpolated. You can use this to scale font sizes, letter spacing, or many other properties
to allow a layout to gracefully cross this gap.

    shim-interpolate(font-size, 10pt, 14pt);
