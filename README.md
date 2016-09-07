# typhen-json-schema [![Build Status](https://secure.travis-ci.org/shiwano/typhen-json-schema.png?branch=master)](http://travis-ci.org/shiwano/typhen-json-schema) [![npm version](https://badge.fury.io/js/typhen-json-schema.svg)](http://badge.fury.io/js/typhen-json-schema)

> Converts TypeScript Interfaces to JSON Schema

## Getting Started
If you haven't used [typhen](https://github.com/shiwano/typhen) before, be sure to check out the README.

```sh
$ npm install --save-dev typhen-json-schema
$ vi tsconfig.json # Add settings.
$ typhen
```

```sh
$ npm install -g typhen-json-schema
$ typhen --plugin typhen-json-schema --dest generated definitions.d.ts
```

## The "typhen-json-schema" plugin

### Overview
In your project's tsconfig.json, add settings for using the plugin.

```js
{
  "files": [
    "src/index.ts"
  ],
  "compilerOptions": {
    "module": "commonjs",
    "target": "ES5"
  },
  "typhen": [
    {
      "plugin": "typhen-json-schema",
      "pluginOptions": {
        "baseUri": "http://example.com/my-schema",
        "enumType": "string"
      },
      "outDir": "output-directory",
      "files": [ "typings/json.d.ts" ]
    }
  ]
}
```

If you want to use an `integer` type of JSON Schema, you will add the interface declaration to the beginning of a file, or add `@integer` tag to number's documentation comments.

```ts
interface integer {}
```

```ts
  /**
    @integer
   */
  age: number;
```

### Options

#### baseUri
Type: `String`
Default value: `''`

The base uri that is used to define a reference to another JSON Schema.

#### enumType
Type: `String`
Default value: `'integer'`

A value that specifies enum value. It is either `string` or `integer`.

### Validations

You can define validation rules by adding tags in documentation comments like the below.

```ts
  /**
    @minimum 0
    @exclusiveMinimum
   */
  price: number;
```

#### string validations

* @minLength {number}
* @maxLength {number}
* @pattern {string}
* @format {string}
* @default {string}

#### number or integer validations

* @multipleOf {number}
* @minimum {number}
* @maximum {number}
* @exclusiveMinimum
* @exclusiveMaximum
* @default {number}

#### object validations

* @minProperties {number}
* @maxProperties {number}

#### array validations

* @minItems {number}
* @maxItems {number}
* @uniqueItems

## Contributing
In lieu of a formal styleguide, take care to maintain the existing coding style. Add unit tests for any new or changed functionality. Lint and test your code using [gulp.js](http://gulpjs.com/).

## Contributors

* Shogo Iwano (@shiwano)
* Horiuchi_H (@horiuchi)
* @nabilnaffar

## License
Copyright (c) 2015 Shogo Iwano
Licensed under the MIT license.
