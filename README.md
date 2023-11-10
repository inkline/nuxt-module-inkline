# Deprecated
### The Inkline Nuxt Module package is now a part of [@inkline/plugin](https://github.com/inkline/plugin).

--- 

<p align="center">
    <a href="http://inkline.io/">
        <img src="https://www.inkline.io/assets/images/logo/logo-black.svg" alt="Inkline logo" width=72 height=72>
    </a>
</p>

<h1 align="center">Inkline - Nuxt Module</h1>

<p align="center">
    Nuxt Module for Inkline, the intuitive UI Components library that gives you the foundation for building high quality, accessible, and customizable Vue.js Design Systems.<br/><br/> Inkline is written and maintained by <a href="https://twitter.com/alexgrozav">@alexgrozav</a>. 
    <br/>
    <br/>
    <a href="https://inkline.io">Homepage</a>
    ·
    <a href="https://inkline.io/docs/introduction">Documentation</a>
    ·
    <a href="https://storybook.inkline.io/">Storybook</a>
    ·
    <a href="https://stackblitz.com/edit/inkline?file=src/App.vue">Playground</a>
    ·
    <a href="https://github.com/inkline/inkline/issues">Issue Tracker</a>
</p>

<br/>
<br/>

## Installation

### 1. **Create a project**

Create a new Nuxt.js application using the `nuxi` CLI command below or using the [Nuxt.js](https://v3.nuxtjs.org/getting-started/installation/) guide, and follow the instructions provided by the installation wizard.

```
npx nuxi init my-nuxt-app

cd my-nuxt-app

npm install
```

### 2. **Install Inkline and dependencies**

Install and save Inkline and the Inkline Nuxt 3 Module as a project dependency.

```
npm install --save @inkline/inkline @inkline/nuxt
```

Inkline uses [Sass](https://sass-lang.com) to pre-process and compile its CSS files. You will need to install it as a development dependency in order to compile the stylesheets.

~~~bash
npm install --save-dev sass
~~~

### 3. **Configure your project**

Open your `nuxt.config.ts` or `nuxt.config.js` file and configure your application to use Inkline.

```js
import { defineNuxtConfig } from 'nuxt';

export default defineNuxtConfig({
    modules: [
        '@inkline/nuxt'
    ],
    inkline: {
        // Plugin options (optional)
    }
});
```

| Property              | Type     | Description                                                               | Default |
|-----------------------|----------|---------------------------------------------------------------------------|---------|
| inkline.css           | Boolean  | Enable or disable adding Inkline's stylesheet automatically.              | true    |
| inkline.sassVariables | String[] | Paths to SCSS Variables to prepend before Inkline's stylesheet.           | []      |
| inkline.global        | Boolean  | Register components to be globally available. This disables tree-shaking. | true    |

### 4. **Configure your design**

Next, open your `app.vue` file and add a style block with the content below. Learn more about the [Design System](https://inkline.io/docs/introduction/design-system).

~~~html
<style lang="scss">
:root {
    --color--primary--h: 195deg;
    --color--primary--s: 77%;
    --color--primary--l: 39%;
}
</style>
~~~

### 5. Enjoy using Inkline

Awesome work! You can now start using all the features that Inkline has to offer.


## Troubleshooting

- **No "exports" defined in ../my-nuxt-app/node_modules/@nuxt/kit/package.json**
    
    Create a patch file called `scripts/patch.js` and run it.

    ~~~js
    const fs = require('fs');
    const path = require('path');

    const target = path.resolve(__dirname, '../node_modules/@nuxt/kit/package.json');
    const contents = fs.readFileSync(target);
    const replaced = contents.toString().replace(
        '"import": "./lib/index.mjs"', 
        '"import": "./lib/index.mjs", "require": "./lib/index.mjs"'
    );

    fs.writeFileSync(target, replaced);
    ~~~

    ~~~bash
    node scripts/patch.js
    ~~~

    Optionally, add it to your **package.json** as a `postinstall` script.

- **Argument of type '{ inkline: {...}; }' is not assignable to parameter of type 'NuxtConfig'**
    
    Create a file called `nuxt-schema-shim.d.ts` and add the following:

    ~~~ts
    import type { PluginConfig } from '@inkline/inkline';

    declare module '@nuxt/schema' {
      interface NuxtConfig {
        inkline?: PluginConfig;
      }
      interface NuxtOptions {
        inkline?: PluginConfig; 
      }
    }
    ~~~

## Creator
**Alex Grozav**

- <https://grozav.com>
- <https://twitter.com/alexgrozav>
- <https://facebook.com/alexgrozav>
- <https://github.com/alexgrozav>

If you use Inkline in your daily work and feel that it has made your life easier, please consider sponsoring me on [Github Sponsors](https://github.com/sponsors/alexgrozav). 💖

## Copyright and license
Code copyright 2017-2022 [Inkline Authors](https://github.com/inkline/inkline/graphs/contributors).
Code released under the [MIT License](https://github.com/inkline/inkline/blob/master/packages/inkline/LICENSE).
