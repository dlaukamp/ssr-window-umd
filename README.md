# SSR Window

Better handling for `window` and `documentt` object in SSR environment.

This library doesn't implement the DOM (like JSDOM), it just patches (or creates `window` and `document` objects) to avoid them to fail (throw errors) during server-side rendering.

Was created for use in:

- [Dom7](https://github.com/nolimits4web/dom7)
- [Swiper](https://github.com/nolimits4web/swiper)
- [Framework7](https://github.com/framework7io/framework7)

## Installation

Library available on NPM:

```
npm i ssr-window
```

## Usage

```js
import { getWindow, getDocument } from 'ssr-window';

const window = getWindow();
const document = getDocument();

window.addEventListener('resize', () => {});

const div = document.querySelectorAll('div');
```

## Extending

If you rely on some window/document properties which are not included here, you can use `extend` helper to add them:

```js
import { ssrWindow, ssrDocument, extend } from 'ssr-window';

// add window.navigator.language
extend(ssrWindow, {
  navigator: {
    language: 'en',
  },
});

// add document.body
extend(ssrDocument, {
  body: {
    /* ... */
  },
});
```

## Contribution

Yes please! See the [contributing guidelines](https://github.com/nolimits4web/ssr-window/blob/master/CONTRIBUTING.md) for details.

## Licence

This project is licensed under the terms of the [MIT license](https://github.com/nolimits4web/ssr-window/blob/master/LICENSE).
