# TastyCSS

CSS-in-JS solution modules that include state-to-style bindings, SSR, and next-level developer experience.

[![NPM Version](https://img.shields.io/npm/v/tastycss.svg?style=flat)](https://www.npmjs.com/package/tastycss)
[![LGTM](https://img.shields.io/lgtm/grade/javascript/github/OutpostHQ/tasty?logo=lgtm&logoWidth=18)](https://lgtm.com/projects/g/OutpostHQ/tasty/)
[![Discord](https://img.shields.io/discord/793832892781690891?color=7389D8&label=chat%20on%20Discord&logo=Discord&logoColor=ffffff)](https://discord.gg/sHnHPnAPZj)

## Installation

```sh
# with npm
npm install tastycss

# with yarn
yarn add tastycss

# with pnpm
pnpm add tastycss
```

## Usage of Tasty API

Let's look at styled API:

```typescript jsx
import { tasty } from 'tastycss';

const Element = tasty({
  /** The tag name of the element. */
  as: 'span',
  /** Default styles of the element. */
  styles: {
    // tokens
    '@local-padding': ['2x', '1x'], // responsive styles
    '@text-color': 'rgba(255, 0, 0)',
    // styles
    padding: '@local-padding',
    color: {
      // the default color
      '': '#text',
      // the color if `blue` mod is specified
      blue: 'blue',
    }, // use color token
  },
  /** Default attributes (example) */
  role: 'article',
  /** The list of styles that can be provided by props */
  styleProps: ['align'],
});
```

Now you can use this element inside your React App:

```typescript jsx
export default function Component({ title, children }) {
  return (
    <>
      <Heading>{title}</Heading>
      <Element>{children}</Element>
    </>
  );
}
```

#### Extend base options

You can use `tasty()` function to extend styling of the existing component.

```typescript jsx
const CustomElement = tasty(Element, {
  /** Change tag name */
  as: 'input',
  /** Extend or rewrite styles */
  styles: {
    color: '#purple',
  },
  /** Add more default properties/attributes */
  role: 'article',
});
```

#### Define global styles

Use `tasty()` to define global styles for elements:

```typescript jsx
import { tasty } from 'tastycss';

const GlobalStyledHeading = tasty('div.myButton', {
  display: 'inline-block',
  padding: '1x 2x',
  preset: 't2',
  border: true,
  radius: true,
});
```

**Documentation is work in progress.**

## Contributing

Please follow our [contributing guidelines](CONTRIBUTING.md).

## License

TastyCSS is a project by [Outpost](https://outpost.run).

Released under the [MIT License](LICENSE).
