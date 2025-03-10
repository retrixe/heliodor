# lunaria

a lightweight and original UI library for Svelte

⚠️ there are no stability guarantees for the API and designs. I don't have the time to satisfy the wider public's use cases (I'm mostly using this in my own projects), so things will remain in flux for now.

## quick start

- Option 1: Copy the components you want out of the library.\
  [Follow the Apache License 2.0 conditions.](https://en.wikipedia.org/wiki/Apache_License#Licensing_conditions)
- Option 2: Add the repository as a git submodule.\
  If doing so, please exempt it from your linting and formatting rules.

I may publish this library in nightly versions for installation via `npm` in the future, so keep a lookout for that if you are pursuing Option 2 (since the project scaffolding will almost certainly break that setup when I do).

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

you may want to include the `Baseline` SCSS file, which:

- enables view transitions for multi-page applications
- sets the system font stack and color scheme
- applies sanity CSS rules from `CssReset` [inspired by Josh Comeau's CSS reset](https://www.joshwcomeau.com/css/custom-css-reset/)
- makes `body` a flexbox occupying the full screen
- applies the above CSS variables to text/backgrounds/links/dividers

note: the components of this library are built according to a 1.5x line height for better legibility. if sizes look off, please include `CssReset` (recommended) or apply this line height to your website where applicable.
