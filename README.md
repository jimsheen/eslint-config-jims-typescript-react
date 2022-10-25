# ESlint configuration for React (Typescript)

## Rules

### no-duplicate-imports

`no-duplicate-imports: 0`

### [`eqeqeq`](https://eslint.org/docs/rules/eqeqeq)

`eqeqeq: ['error', 'always', { null: 'ignore' }]`

**Incorrect**

```js
a == b;
foo == true;
bananas != 1;
value == undefined;
typeof foo == 'undefined';
'hello' != 'world';
0 == 0;
true == true;
```

**Correct**

```js
a === b;
foo === true;
bananas !== 1;
value === undefined;
typeof foo === 'undefined';
'hello' !== 'world';
0 === 0;
true === true;
foo == null;
```

### [`import/first`](https://github.com/benmosher/eslint-plugin-import/blob/master/docs/rules/first.md)

`'import/first': ['warn']`

**Incorrect**

```js
import foo from './foo';

// some module-level initializer
initWith(foo);

import bar from './bar'; // <- reported
```

or

```js
import foo from 'foo';
import bar from './bar';

import * as _ from 'lodash'; // <- reported
```

### [`import/newline-after-import`](https://github.com/benmosher/eslint-plugin-import/blob/master/docs/rules/newline-after-import.md)

`'import/newline-after-import': ['warn', { count: 1 }]`

**Incorrect**

```js
import * as foo from 'foo';
const FOO = 'BAR';
```

or

```js
import * as foo from 'foo';
const FOO = 'BAR';

import { bar } from 'bar-lib';
```

or

```js
const FOO = require('./foo');
const BAZ = 1;
const BAR = require('./bar');
```

**Correct**

```js
import defaultExport from './foo';

const FOO = 'BAR';
```

or

```js
import { bar } from 'bar-lib';

import defaultExport from './foo';

const FOO = 'BAR';
```

### [`import/prefer-default-export`](https://github.com/import-js/eslint-plugin-import/blob/main/docs/rules/prefer-default-export.md)

`'import/prefer-default-export': 'off'`

### [`import/group-exports`](https://github.com/import-js/eslint-plugin-import/blob/main/docs/rules/group-exports.md)

`'import/group-exports': 'off'`

### [`import/no-unresolved`](https://github.com/benmosher/eslint-plugin-import/blob/master/docs/rules/no-unresolved.md)

`'import/no-unresolved': ['error', { commonjs: true, caseSensitive: true }]`

```js
import x from './foo'; // reports if './foo' cannot be resolved on the filesystem
```

```js
require(['x', 'y'], function (x, y) {
  /*...*/
}); // ignored
```

```js
const { default: x } = require('./foo'); // reported if './foo' is actually './Foo'
```

### [`no-console`](https://eslint.org/docs/rules/no-console)

`'no-console': ['error', { allow: ['info', 'warn', 'error'] }]`

**Incorrect**

```js
console.log('Log a debug level message.');
```

**Correct**

```js
console.info('Log an info level message.');
console.warn('Log a warn level message.');
console.error('Log an error level message.');
```

### [`no-debugger`](https://eslint.org/docs/rules/no-debugger)

`'no-debugger': 'error'`

**Incorrect**

```js
function isTruthy(x) {
  debugger;
  return Boolean(x);
}
```

### [`no-unused-vars`](https://eslint.org/docs/rules/no-unused-vars)

```
'no-unused-vars': 'off'
```

### [`@typescript-eslint/no-unused-vars`](https://github.com/typescript-eslint/typescript-eslint/blob/main/packages/eslint-plugin/docs/rules/no-unused-vars.md)

```
'@typescript-eslint/no-unused-vars': ['warn', { ignoreRestSiblings: true }]
```

**Incorrect**

```js
// It checks variables you have defined as global
some_unused_var = 42

const x

// Write-only variables are not considered as used.
let y = 10
y = 5

// A read for a modification of itself is not considered as used.
let z = 0
z = z + 1

// By default, unused arguments cause warnings.
(function(foo) {
  return 5
})()

// Unused recursive functions also cause warnings.
function fact(n) {
  if (n < 2) return 1
  return n * fact(n - 1)
}

// When a function definition destructures an array, unused entries from the array also cause warnings.
function getY([x, y]) {
  return y
}

// "baz" is defined but never used
(function(foo, bar, baz) {
  return bar
})()
```

**Correct**

```js
const x = 10;
alert(x);

// foo is considered used here
myFunc(
  function foo() {
    // ...
  }.bind(this),
)(function (foo) {
  return foo;
})();

let myFunc;
myFunc = setTimeout(function () {
  // myFunc is considered used
  myFunc();
}, 50);

// Only the second argument from the descructured array is used.
function getY([, y]) {
  return y;
}

(function (foo, bar, baz) {
  return baz;
})();

// 'type' is ignored because it has a rest property sibling.
const { type, ...coords } = data;
```

### [`@typescript-eslint/no-use-before-define`](https://github.com/typescript-eslint/typescript-eslint/blob/main/packages/eslint-plugin/docs/rules/no-use-before-define.md)

`'@typescript-eslint/no-use-before-define': 'off'`

### [`@typescript-eslint/explicit-function-return-type`](https://github.com/typescript-eslint/typescript-eslint/blob/main/packages/eslint-plugin/docs/rules/explicit-function-return-type.md)

`'@typescript-eslint/explicit-function-return-type': 'off'`

### [`@typescript-eslint/no-non-null-assertion`](https://github.com/typescript-eslint/typescript-eslint/blob/main/packages/eslint-plugin/docs/rules/no-non-null-assertion.md)

`'@typescript-eslint/no-non-null-assertion': 'off'`

### [`@typescript-eslint/ban-types`](https://github.com/typescript-eslint/typescript-eslint/blob/main/packages/eslint-plugin/docs/rules/ban-types.md)

`'@typescript-eslint/ban-types': 'off'`

### [`@typescript-eslint/explicit-module-boundary-types`](https://github.com/typescript-eslint/typescript-eslint/blob/main/packages/eslint-plugin/docs/rules/explicit-module-boundary-types.md)

`'@typescript-eslint/explicit-module-boundary-types': 'off'`

### [`@typescript-eslint/no-explicit-any`](https://github.com/typescript-eslint/typescript-eslint/blob/main/packages/eslint-plugin/docs/rules/no-explicit-any.md)

`'@typescript-eslint/no-explicit-any': 'error'`

### [`no-restricted-imports`](https://eslint.org/docs/rules/no-restricted-imports)

```
'no-restricted-imports': [
  'error',
  {
    paths: [
      {
        name: 'styled-components',
        message: 'Please import from styled-components/macro.',
      },
    ],
    patterns: ['!styled-components/macro'],
  },
]
```

### [`import/no-named-as-default-member`](https://github.com/import-js/eslint-plugin-import/blob/main/docs/rules/no-named-as-default-member.md)

`'import/no-named-as-default-member': 0`

### [`import/order`](https://github.com/import-js/eslint-plugin-import/blob/main/docs/rules/order.md)

```
'import/order': [
  'warn',
  {
    pathGroups: [
      {
        pattern: '@material-ui/**',
        group: 'external',
        position: 'after',
      },
      {
        pattern: '@',
        group: 'internal',
        position: 'before',
      },
    ],
    'newlines-between': 'always-and-inside-groups',
    pathGroupsExcludedImportTypes: ['external'],
    groups: ['external', 'unknown', 'internal', ['sibling', 'parent'], 'builtin', 'index', 'object', 'type'],
  },
]
```

### [`curly`](https://eslint.org/docs/rules/curly)

`curly: 'error'`

### [`padding-line-between-statements`](https://eslint.org/docs/rules/padding-line-between-statements)

```
'padding-line-between-statements': [
  'error',
  {
    blankLine: 'always',
    prev: [
      'block',
      'block-like',
      'class',
      'const',
      'continue',
      'debugger',
      'default',
      'do',
      'empty',
      'for',
      'function',
      'if',
      'iife',
      'import',
      'let',
      'return',
      'switch',
      'throw',
      'try',
      'var',
      'while',
      'with',
    ],
    next: '*',
  },
  {
    blankLine: 'any',
    prev: ['const', 'let', 'var', 'import', 'export'],
    next: ['const', 'let', 'var', 'import', 'export'],
  },
  {
    blankLine: 'always',
    prev: ['*'],
    next: ['return'],
  },
]
```

### [`react/jsx-sort-props`](https://github.com/jsx-eslint/eslint-plugin-react/blob/master/docs/rules/jsx-sort-props.md)

```
'react/jsx-sort-props': [
  'warn',
  {
    ignoreCase: false,
    callbacksLast: true,
    shorthandFirst: true,
    reservedFirst: true,
  },
]
```

### [`prettier/prettier`](https://github.com/prettier/eslint-config-prettier)

### [`rest-spread-spacing`](https://eslint.org/docs/rules/rest-spread-spacing)

`'rest-spread-spacing': ['error', 'never']`

**Incorrect**

```js
fn(... args)
[... arr, 4, 5, 6]
let [a, b, ... arr] = [1, 2, 3, 4, 5]
function fn(... args) { console.log(args) }
let { x, y, ... z } = { x: 1, y: 2, a: 3, b: 4 }
let n = { x, y, ... z }
```

**Correct**

```js
fn(...args)
[...arr, 4, 5, 6]
let [a, b, ...arr] = [1, 2, 3, 4, 5]
function fn(...args) { console.log(args) }
let { x, y, ...z } = { x: 1, y: 2, a: 3, b: 4 }
let n = { x, y, ...z }
```

### [`template-curly-spacing`](https://eslint.org/docs/rules/template-curly-spacing)

`'template-curly-spacing': 'error'`

**Incorrect**

```js
`hello, ${people.name}!``hello, ${people.name}!``hello, ${people.name}!`;
```

**Correct**

```js
`hello, ${people.name}!``hello, ${people.name}!`;
```

# Prettier recommended configuration

```
{
  "semi": true,
  "trailingComma": "all",
  "singleQuote": true,
  "printWidth": 120,
  "tabWidth": 2,
  "bracketSpacing": true,
  "endOfLine": "auto"
}
```
