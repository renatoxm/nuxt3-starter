# Nuxt 3 Starter

A Nuxt 3 starter template or boilerplate with a lot of useful features. and integrated with TailwindCSS 3.

## Features

- [x] 💨 [Tailwind CSS v3](https://tailwindcss.com/) with [Windicss](https://windicss.org/)
- [x] ✨ [Headless UI](https://headlessui.dev/)
- [x] 🔔 [Icon Pack Component (unplugin-icons)](https://icones.js.org/)
- [x] 🛹 [State & Store Management (Pinia)](https://pinia.vuejs.org/)
- [x] 🚩 [Localization (i18n) by @intlify](https://github.com/intlify/nuxt3) & Auto Generate Locales
- [x] 📦 [Vue Composition Collection (Vueuse)](https://vueuse.org/)
- [x] 📚 [Content Management System (Nuxt Content)](https://content.nuxtjs.org/) [SSR]
- [x] 🌙 Switch Theme (light, dark, system, realtime)
- [x] 🇮🇩 Language Switcher
- [x] 🪝 Built-in Component & Layout
- [x] Eslint & Prettier
- [x] Husky & Commitlint
- [x] Custom Workspace Snippets
- [x] Built-in Unit Test
- [x] Configurable Theme
- [x] Primary Colors
- [x] Font

## Preview

<table align="center">
  <tr>
    <td align="center" width="95%" colspan="2">
      <img src="https://github.com/renatoxm/nuxt3-starter/blob/main/assets/images/Nuxt3StarterScreen.png?raw=true" alt="Preview" title="Preview">
    </td>
  </tr>
</table>
<p align="center">
  <br>
  <a href="https://nuxt3-starter.vercel.app/" target="_blank">
    Live Demo
  </a>
  <br><br>
  <a href="https://codesandbox.io/s/github/renatoxm/nuxt3-starter" title="Open In Code Sandbox">
    <img src="https://img.shields.io/badge/Open%20in-CodeSandbox-blue?style=flat-square&logo=codesandboxg" alt="Open In Code Sandbox">
  </a>
</p>

## Table of Contents

- [Nuxt 3 Starter](#nuxt-3-starter)
  - [Features](#features)
  - [To Do](#to-do)
  - [Preview](#preview)
  - [Table of Contents](#table-of-contents)
  - [Quick Start](#quick-start)
    - [Start with this template](#start-with-this-template)
    - [Deploy as Static Site](#deploy-as-static-site)
  - [Built-in Components](#built-in-components)
  - [Notes](#notes)
    - [Nuxt Content](#nuxt-content)
    - [Custom Workspace Snippets](#custom-workspace-snippets)
    - [Styles](#styles)
    - [Theme (Dark Mode)](#theme-dark-mode)
    - [Localization](#localization)
    - [Generate Locales](#generate-locales)
    - [Icons](#icons)
    - [Precommit and Postmerge](#precommit-and-postmerge)
  - [License](#license)

## Quick Start

For detail information, go here [Getting Started](https://nuxt3-starter.vercel.app/getting-started)

### Start with this template

- This project using `pnpm` as package manager.
- Clone this project to your computer `git clone https://github.com/renatoxm/nuxt3-starter`
- Install dependencies `pnpm install --shamefully-hoist`
- Run `pnpm dev` to start development server and open `http://localhost:3000` in your browser

### Deploy as Static Site

- Run `pnpm generate` to build the project
- Serve `dist/` folder
  Checkout the [deployment documentation](https://v3.nuxtjs.org/docs/deployment).

## Built-in Components

- [x] Footer
- [x] Button
- [x] Anchor (link)
- [x] Alert
- [x] Card
- [x] Action Sheet
- [x] Theme Toggle / Switcher
- [x] Navbar
  - [x] Navbar Builder
  - [x] Drawer (on mobile)
  - [x] Options (on mobile)
- [x] Page Layout
  - [x] Wrapper
  - [x] Header
    - [x] Title
  - [x] Body
    - [x] Section
      - [x] Section Wrapper
      - [x] Section Title
- [x] Dashboard Layout
  - [x] Sidebar
- [ ] Modal

## Notes

### Nuxt Content

With Nuxt Content, you can just create markdown file (recommended) inside `content` folder.  
But this is only available for SSR (Server Side Rendering) mode. Static mode still not working, you can see the issue https://github.com/nuxt/content/issues/1202
For now, you can follow

### Custom Workspace Snippets

This workspace including custom snippets for VSCode.

- **n3:content**  
  content template with markdown
- **n3:page**  
  page template

### Styles

Tailwindcss import managed by windicss.
and you can add custom styles in :

```
/path/to/assets/sass/app.scss
```

### Theme (Dark Mode)

ThemeManager is a plugin that allows you to switch between themes. this lib in :

```
/path/to/utils/theme.ts
```

`Thememanager` is a function-class construct when app.vue before mounted. theme construct inside `AppSetup()` in `/path/to/app.vue` :

```vue
<!-- /path/to/app.vue -->
<script lang="ts" setup>
import { AppSetup } from '~/utils/app'
// app setup
AppSetup()
</script>
```

To change theme, you can direct set theme from state `theme.setting`, example :

```vue
<script lang="ts" setup>
import { IThemeSettingOptions } from '~/utils/theme'
const themeSetting = useState<IThemeSettingOptions>('theme.setting')
themeSetting.value = 'dark'
</script>
```

When you change state `theme.setting`, it will automatically change theme.

Theme Setting have 4 options :

- `light`
- `dark`
- `system` (operating system theme)
- `realtime` (realtime theme, if 05:00 - 17:00, it will change to light theme, otherwise dark)

We have state `theme.current`, this state return `light` or `dark` theme. basically it's process from `theme.setting`.
dont change theme with this state.

### Localization

Localization is a plugin that allows you to switch between languages. this lib in :

```
/path/to/utils/lang.ts
```

`LanguageManager` is a function-class construct when app.vue before mounted.
this lib depend on [@intlify/nuxt3](https://github.com/intlify/nuxt3)
lang construct inside `AppSetup()` in `/path/to/app.vue` :

<!-- /path/to/app.vue -->
<script lang="ts" setup>
import { AppSetup } from '~/utils/app';
// app setup
AppSetup()
</script>

To change language, you can direct set language from state `lang.setting`, example :

```vue
<script lang="ts" setup>
const langSetting = useState<string>('locale.setting')
langSetting.value = 'en'
</script>
```

When you change state `locale.setting`, it will automatically change language.

### Generate Locales

I made an automatic tool to automatically translate to all languages ​​that have been prepared in the ./locales/ folder
So, you can just update "locales/en.yml" and run this tools, it will automatically translate to all languages.

You can just run :

```
pnpm generate:locales

# or :

node ./tools/translator.js ./locales en.yml
```

### Icons

This project using unplugin-icons for auto generate and import icon as component.

You can see collection icon list in : [https://icones.js.org/](https://icones.js.org/)

you can use `<prefix-collection:icon />` or `<PrefixCollection:Icon />`.

in this project, configuration prefix as a "icon", you can see in `nuxt.config.ts` :

```js
export default defineNuxtConfig({
    ...

    vite: {
        plugins: [
            UnpluginComponentsVite({
                dts: true,
                resolvers: [
                    IconsResolver({
                        prefix: 'Icon',
                    }),
                ],
            }),
        ],
    },

    ...
})
```

Example :

```vue
// use icon from collection "Simple Icons" and name icon is "nuxtdotjs"
<IconSimpleIcons:nuxtdotjs />

// use icon from collection "Unicons" and name icon is "sun"
<IconUil:sun />
```

### Precommit and Postmerge

This project using husky and commitlint for precommit and postmerge.
when you commit, it will check your commit message and running "pnpm lint-staged" to check your staged files.
configuration in : `/path/to/.husky/pre-commit` and `/path/to/commitlint.config.js`

And when Postmerge, it will run "pnpm" to automatically install new dependencies.
configuration in `/path/to/.husky/post-merge`

## Credits

This project was based on the beautifully crafted [Nuxt 3 Awesome Starter](https://github.com/viandwi24/nuxt3-awesome-starter) by [Alfian Dwi Nugraha](https://github.com/viandwi24)

## License

This project is licensed under the MIT license, Copyright (c) 2023 Renato Nabinger. For more information see the [LICENSE](LICENSE.md) file.

