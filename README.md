# JungleJS + Storybook + TailwindCSS starter site

<img src="https://image.flaticon.com/icons/svg/2950/2950532.svg" width="120" height="120" alt="" />

A starter site for:

- [JungleJS](https://www.junglejs.org) — Svelte and GraphQL-based static site generator
- [Storybook](https://storybook.js.org) — UI development environment
- [TailwindCSS](https://tailwindcss.com) — utility-first CSS framework

## Installation

```bash
git clone https://github.com/ekafyi/junglejs-storybook-tailwind.git
cd junglejs-storybook-tailwind

# Install dependencies
npm install

# Start Jungle server
npm run start

# Start Storybook server
npm run storybook
```

Jungle runs on `localhost:3000`.

Storybook runs on `localhost:6006`.

## Directory structure

```sh
root
├── .storybook # Storybook config
├── src
│   ├── # ... Jungle components & routes dir
│   ├── stories # Storybook sample stories
│   ├── tailwind.css # Tailwind source file
│   └── template.html # Jungle template (with global.css swapped for tailwind.css)
├── static
│   ├── # ... other Jungle assets
│   ├── global.css # default Jungle CSS (not used)
│   └── tailwind.css # Tailwind output/generated file
├── # ... default jungle & package files
├── postcss.config.js
└── tailwind.config.js
```

This starter uses as much default settings & file structure as possible. Only custom configuration files are shown above.

## Storybook

**.storybook/main.js**

In this starter, your Storybook files should have the extension `.stories.js`. The default sample stories are in `src/stories`, but you can move it anywhere within the `src` directory. You can override this configuration and add further customization in `.storybook/main.js`. More info: https://storybook.js.org/docs/configurations/overview

**.storybook/preview.js**

This file contains decorators for the `@storybook/addon-a11y` addon.

**.storybook/preview-head.html**

This file adds the generated CSS file (`tailwind.css`). Tailwind by default includes normalize and base styles, so [Jungle global CSS](https://github.com/junglejs/junglejs/blob/master/example/static/global.css) is not necessary; I leave it commented out.
More info: https://storybook.js.org/docs/configurations/add-custom-head-tags

## Tailwind

This starter uses Tailwind with PostCSS on its own, NOT integrated to Storybook [custom webpack config](https://storybook.js.org/docs/configurations/custom-webpack-config/) nor to [Jungle config](https://github.com/ekafyi/junglejs-storybook-tailwind/blob/master/jungle.config.js). We simply run and watch for changes during development (`start` and `storybook` commands), and generate an optimized build version in `build` and `build-storybook`. Open `package.json` to see or modify the commands.

**src/tailwind.css**

Source Tailwind file. Add your additional global styles here.

**src/static/tailwind.css**

Output/generated Tailwind file. You should not be modifying this. It is minified during production.

**postcss.config.js**

PostCSS configuration file. [cssnano](https://cssnano.co/) (PostCSS minifier) and [autoprefixer](https://github.com/postcss/autoprefixer) are only run during production (`npm run build:css`). More info: https://tailwindcss.com/docs/using-with-preprocessors/#using-postcss-as-your-preprocessor

**tailwind.config.js**

Tailwind configuration file. The `purge` object defines what files are checked when “purging” (removing unused Tailwind classes in production).

More info:

- https://tailwindcss.com/docs/configuration
- https://tailwindcss.com/docs/controlling-file-size/

## Credits

Boilerplate code from [Jungle template](https://github.com/junglejs/template). Icon in this readme by [Freepik](http://www.freepik.com) from [Flaticon](https://www.flaticon.com).

---

(c) 2020 Eka MIT License
