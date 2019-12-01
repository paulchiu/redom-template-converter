# RE:DOM HTML to JavaScript converter

## Forked From

[Mithril HTML to JavaScript converter](https://github.com/ArthurClemens/mithril-template-converter)

## Online Converter

(To do)

## Getting Started

### Set Up and Build

The following assumes you are developing the online converter application. The commands will run the local dev server at `http://0.0.0.0:4000`.

```
npm i
npx lerna bootstrap
cd packages/app
npm run dev
```

### App

Contains source code for the online converter, located in `./packages/app`.

Helper patterns and libraries:

* [Meiosis](http://meiosis.js.org)
* [Patchinko](https://github.com/barneycarroll/patchinko)
* [Polythene](http://polythene.js.org)

### Template Builder

Helper function to create Mithril templates from HTML. Use the output text to copy-paste into your source code, located in `./packages/mithril-template-builder`.

```javascript
/**
 * @param {object} opts 
 * @param {string} opts.source - String containing HTML markup
 * @param {("2" | "4" | "tab")} opts.indent - Indent spacing
 * @param {("double" | "single")} opts.quotes - Quotes
 * @param {("attributes" | "selectors")} opts.attrs - Display of attributes
 * @returns {string}
 */
const resultString = templateBuilder(opts)
```

### Usage in modules

```javascript
import { templateBuilder } from "mithril-template-builder"

const source = `
<p>Mithril website: <a href="http://mithril.js.org">Mithril website</a></p>
`
const output = templateBuilder({
  source
})
```

Output:
```javascript
m("p",
  [
    "Mithril website: ",
    m("a", {"href":"http://mithril.js.org"}, 
      "Mithril website"
    )
  ]
)
```

```javascript
import { templateBuilder } from "mithril-template-builder"

const source = `
<a href="http://mithril.js.org">Mithril</a>
`
const output = templateBuilder({
  source,
  indent: "4",
  attrs: "selectors",
  quotes: "single",
})
```

Output:

```javascript
m('a[href="http://mithril.js.org"]', 
    'Mithril'
)
```
