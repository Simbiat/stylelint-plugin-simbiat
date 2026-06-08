# stylelint-plugin-simbiat

Custom Stylelint rules that are used in the [simbiat.eu](https://github.com/Simbiat/simbiat.ru) project. Created with the use of Claude AI (I am realistically not that proficient) but manually reviewed, adjusted, and tested on the existing codebase.

## Installation

```bash
npm install --save-dev @simbiat/stylelint-plugin-simbiat
```

Requires ESLint
`>=14.0.0`, and postcss-selector-parser `>=6.0.0`.

---

## Usage (flat config)

```js
export default {
  extends: 'stylelint-config-standard',
  plugins: [
    'stylelint-plugin-simbiat',
  ],
  rules: {
    'simbiat/require-attribute-i-flag': [true, { severity: 'warning' }],
  },
}
```

---

## Rules

### `simbiat/require-attribute-i-flag` - *suggestion*

Requires the
`i` (case-insensitive) flag on every attribute-value selector that carries a value comparison operator and a non-empty value.

Selectors with no operator (presence-only, e.g. `[hidden]`) or with the flag already present are left alone.

Fixable: yes - appends ` i` before the closing `]`.