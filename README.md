# heliodor

a lightweight and original UI library for Svelte

⚠️ there are no stability guarantees for the API and designs. I don't have the time to satisfy the wider public's use cases (I'm mostly using this in my own projects), so things will remain in flux for now.

## quick start

- Option 1: Copy the components you want out of the library.\
  [Follow the Apache License 2.0 conditions.](https://en.wikipedia.org/wiki/Apache_License#Licensing_conditions)
- Option 2: Install nightly versions of Heliodor from npm via `npm install heliodor` and import the components you want to use.\
  Alternatively, use `yarn add heliodor` or `pnpm add heliodor` if you prefer those package managers.

## documentation

currently, there is none, but the components are straightforward to use.

the following CSS variables must be set by you:

```scss
/* These colors are just examples using a shade of blue as the primary color */
:root {
  --primary-color: #0080ff;
  --error-color: #ff0042;

  --link-color: #0080ff;
  --background-color: #f5f5f5; /* White smoke */
  --surface-color: #fcfcfc; /* White smoke but brighter */
  --color: #000000;
  --divider-color: #bbb;

  @media (prefers-color-scheme: dark) {
    --link-color: #00bfff;
    --background-color: #0e0e10; /* Jet black */
    --surface-color: #1b1b1b; /* Eerie black */
    --color: #ffffff;
    --divider-color: #666;
  }
}
```

you may want to include the `heliodor/Baseline.scss` SCSS file, which:

- enables view transitions for multi-page applications
- sets the system font stack and color scheme
- applies sanity CSS rules from `heliodor/CssReset.scss` [inspired by Josh Comeau's CSS reset](https://www.joshwcomeau.com/css/custom-css-reset/)
- makes `body` a flexbox occupying the full screen
- applies the above CSS variables to text/backgrounds/links/dividers

note: the components of this library are built according to a 1.5x line height for better legibility. if sizes look off, please include `CssReset` (recommended) or apply this line height to your website where applicable.
