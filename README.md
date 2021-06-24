# [react-currency-hooks](https://github.com/cool-hooks/react-currency-hooks)

[![NPM version](https://img.shields.io/npm/v/react-currency-hooks?style=flat-square)](https://www.npmjs.com/package/react-currency-hooks)
[![NPM downloads](https://img.shields.io/npm/dm/react-currency-hooks?style=flat-square)](https://www.npmjs.com/package/react-currency-hooks)
[![NPM license](https://img.shields.io/npm/l/react-currency-hooks?style=flat-square)](https://www.npmjs.com/package/react-currency-hooks)
[![Codecov](https://img.shields.io/codecov/c/github/cool-hooks/react-currency-hooks?style=flat-square)](https://codecov.io/gh/cool-hooks/react-currency-hooks)
[![Travis](https://img.shields.io/travis/cool-hooks/react-currency-hooks/master?style=flat-square)](https://travis-ci.org/cool-hooks/react-currency-hooks)
[![Bundle size](https://img.shields.io/bundlephobia/min/react-currency-hooks?style=flat-square)](https://bundlephobia.com/result?p=react-currency-hooks)

## About

Currency converter React hook

### Demo

**[Playground – play with library in CodeSandbox](https://codesandbox.io/s/react-currency-hooks-l3b1l)**

### Similar Projects

- [Cashify](https://github.com/xxczaki/cashify/) by [Antoni Kepinski](https://github.com/xxczaki/)
- [money.js](https://github.com/openexchangerates/money.js/) by [Open Exchange Rates](https://github.com/openexchangerates/)

## How to Install

First, install the library in your project by npm:

```sh
$ npm install react-currency-hooks
```

Or Yarn:

```sh
$ yarn add react-currency-hooks
```

## Getting Started

**• Import hook in React application file:**

```js
import { useCurrency } from 'react-currency-hooks';
```

#### Params

| Name        | Type   | Default | Description                |
| ----------- | ------ | ------- | -------------------------- |
| **amount**  | number | ` `     | Amount of money to convert |
| **options** | {}     | ` `     | Convertion options         |

#### Options

| Name              | Type               | Default | Description                                                               |
| ----------------- | ------------------ | ------- | ------------------------------------------------------------------------- |
| **from**          | string             | ` `     | Currency to be converted                                                  |
| **to**            | string or string[] | ` `     | The currency to which it is converted                                     |
| **base**          | string             | ` `     | Base currency                                                             |
| **rates**         | Rates              | `{}`    | Currency rates                                                            |
| **keepPrecision** | boolean            | `true`  | `true` (return exact values), `false` (return values rounded to 2 places) |

#### Returned Values

| Type                                            | Description     |
| ----------------------------------------------- | --------------- |
| number or object with currencies passed in `to` | Converted value |

## Example

```js
import React from 'react';
import { useCurrency } from 'react-currency-hooks';

const App = () => {
  const rates = {
    GBP: 0.92,
    EUR: 1.0,
    CHF: 1.08,
    USD: 1.12,
  };

  /*
   * 1. With single `to` value
   */
  const currency = useCurrency(200, {
    from: 'USD',
    to: 'CHF',
    base: 'EUR',
    rates,
  });

  return <p>USD to CHF: {currency}</p>;

  /*
   * 2. With multiple `to` values
   */
  const { chf, gbp } = useCurrency(200, {
    from: 'USD',
    to: ['CHF', 'GBP'],
    base: 'EUR',
    rates,
  });

  return (
    <>
      <p>USD to CHF: {chf}</p>
      <p>USD to GBP: {gbp}</p>
    </>
  );
};

export default App;
```

## License

This project is licensed under the MIT License © 2020-present Jakub Biesiada
