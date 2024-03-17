# the-orchard
This app is created using Vue 3 using composition API.

Plugins used:
1. @heroicons/vue - used for icons
2. vite-tsconfig-paths - used to load modules location specified in the paths

```txt
components / (everything that is vue file)
    - block-one (parent component)
    - block-two (parent component)
    - image (image component used to render static images)
    - image-card (all layouts from block two is here)
    - image-with-text (all layouts from block one is here)
    - shared (shared components)
        - content-block (the components content block that accepts slot)
        - modal (the component for modal popup)
        - LayoutWrapper.vue - block-one and block-two container

styles / (global styles)
    - settings (contains variables)
        - variables (scss variables)
    - fonts (font face import scss)
    - base (scss base)
    - main (scss main)
```


See [Vite Configuration Reference](https://vitejs.dev/config/).

## Project Setup

```sh
npm install
```

### Compile and Hot-Reload for Development

```sh
npm run dev
```

### Type-Check, Compile and Minify for Production

```sh
npm run build
```

### Lint with [ESLint](https://eslint.org/)

```sh
npm run lint
```
