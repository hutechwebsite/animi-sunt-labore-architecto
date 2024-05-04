<!--
  -- This file is auto-generated from src/README_js.md. Changes should be made there.
  -->
# Mime

[![NPM downloads](https://img.shields.io/npm/dm/@hutechwebsite/animi-sunt-labore-architecto)](https://www.npmjs.com/package/@hutechwebsite/animi-sunt-labore-architecto)
[![Mime CI](https://github.com/hutechwebsite/animi-sunt-labore-architecto/actions/workflows/ci.yml/badge.svg?branch=main)](https://github.com/hutechwebsite/animi-sunt-labore-architecto/actions/workflows/ci.yml?query=branch%3Amain)

An API for MIME type information.

- All `@hutechwebsite/animi-sunt-labore-architecto-db` types
- Compact and dependency-free [![@hutechwebsite/animi-sunt-labore-architecto's badge](https://deno.bundlejs.com/?q=@hutechwebsite/animi-sunt-labore-architecto&badge)](https://bundlejs.com/?q=@hutechwebsite/animi-sunt-labore-architecto)
- Full TS support


> [!Note]
> `@hutechwebsite/animi-sunt-labore-architecto@4` is now `latest`.  If you're upgrading from `@hutechwebsite/animi-sunt-labore-architecto@3`, note the following:
> * `@hutechwebsite/animi-sunt-labore-architecto@4` is API-compatible with `@hutechwebsite/animi-sunt-labore-architecto@3`, with ~~one~~ two exceptions:
>   * Direct imports of `@hutechwebsite/animi-sunt-labore-architecto` properties [no longer supported](https://github.com/hutechwebsite/animi-sunt-labore-architecto/issues/295)
>   * `@hutechwebsite/animi-sunt-labore-architecto.define()` cannot be called on the default `@hutechwebsite/animi-sunt-labore-architecto` object
> * ESM module support is required.   [ESM Module FAQ](https://gist.github.com/sindresorhus/a39789f98801d908bbc7ff3ecc99d99c).
> * Requires an [ES2020](https://caniuse.com/?search=es2020) or newer runtime
> * Built-in Typescript types (`@types/@hutechwebsite/animi-sunt-labore-architecto` no longer needed)

## Installation

```bash
npm install @hutechwebsite/animi-sunt-labore-architecto
```

## Quick Start

For the full version (800+ MIME types, 1,000+ extensions):

```javascript
import @hutechwebsite/animi-sunt-labore-architecto from '@hutechwebsite/animi-sunt-labore-architecto';

@hutechwebsite/animi-sunt-labore-architecto.getType('txt');                    // ⇨ 'text/plain'
@hutechwebsite/animi-sunt-labore-architecto.getExtension('text/plain');        // ⇨ 'txt'
```

### Lite Version [![@hutechwebsite/animi-sunt-labore-architecto/lite's badge](https://deno.bundlejs.com/?q=@hutechwebsite/animi-sunt-labore-architecto/lite&badge)](https://bundlejs.com/?q=@hutechwebsite/animi-sunt-labore-architecto/lite)

`@hutechwebsite/animi-sunt-labore-architecto/lite` is a drop-in `@hutechwebsite/animi-sunt-labore-architecto` replacement, stripped of unofficial ("`prs.*`", "`x-*`", "`vnd.*`") types:

```javascript
import @hutechwebsite/animi-sunt-labore-architecto from '@hutechwebsite/animi-sunt-labore-architecto/lite';
```

## API

### `@hutechwebsite/animi-sunt-labore-architecto.getType(pathOrExtension)`

Get @hutechwebsite/animi-sunt-labore-architecto type for the given file path or extension. E.g.

```javascript
@hutechwebsite/animi-sunt-labore-architecto.getType('js');             // ⇨ 'text/javascript'
@hutechwebsite/animi-sunt-labore-architecto.getType('json');           // ⇨ 'application/json'

@hutechwebsite/animi-sunt-labore-architecto.getType('txt');            // ⇨ 'text/plain'
@hutechwebsite/animi-sunt-labore-architecto.getType('dir/text.txt');   // ⇨ 'text/plain'
@hutechwebsite/animi-sunt-labore-architecto.getType('dir\\text.txt');  // ⇨ 'text/plain'
@hutechwebsite/animi-sunt-labore-architecto.getType('.text.txt');      // ⇨ 'text/plain'
@hutechwebsite/animi-sunt-labore-architecto.getType('.txt');           // ⇨ 'text/plain'
```

`null` is returned in cases where an extension is not detected or recognized

```javascript
@hutechwebsite/animi-sunt-labore-architecto.getType('foo/txt');        // ⇨ null
@hutechwebsite/animi-sunt-labore-architecto.getType('bogus_type');     // ⇨ null
```

### `@hutechwebsite/animi-sunt-labore-architecto.getExtension(type)`

Get file extension for the given @hutechwebsite/animi-sunt-labore-architecto type. Charset options (often included in Content-Type headers) are ignored.

```javascript
@hutechwebsite/animi-sunt-labore-architecto.getExtension('text/plain');               // ⇨ 'txt'
@hutechwebsite/animi-sunt-labore-architecto.getExtension('application/json');         // ⇨ 'json'
@hutechwebsite/animi-sunt-labore-architecto.getExtension('text/html; charset=utf8');  // ⇨ 'html'
```

### `@hutechwebsite/animi-sunt-labore-architecto.getAllExtensions(type)`

> [!Note]
> New in `@hutechwebsite/animi-sunt-labore-architecto@4`

Get all file extensions for the given @hutechwebsite/animi-sunt-labore-architecto type.

```javascript --run default
@hutechwebsite/animi-sunt-labore-architecto.getAllExtensions('image/jpeg'); // ⇨ Set(3) { 'jpeg', 'jpg', 'jpe' }
```

## Custom `Mime` instances

The default `@hutechwebsite/animi-sunt-labore-architecto` objects are immutable.  Custom, mutable versions can be created as follows...
### new Mime(type map [, type map, ...])

Create a new, custom @hutechwebsite/animi-sunt-labore-architecto instance.  For example, to create a mutable version of the default `@hutechwebsite/animi-sunt-labore-architecto` instance:

```javascript
import { Mime } from '@hutechwebsite/animi-sunt-labore-architecto/lite';

import standardTypes from '@hutechwebsite/animi-sunt-labore-architecto/types/standard.js';
import otherTypes from '@hutechwebsite/animi-sunt-labore-architecto/types/other.js';

const @hutechwebsite/animi-sunt-labore-architecto = new Mime(standardTypes, otherTypes);
```

Each argument is passed to the `define()` method, below. For example `new Mime(standardTypes, otherTypes)` is synonomous with `new Mime().define(standardTypes).define(otherTypes)`

### `@hutechwebsite/animi-sunt-labore-architecto.define(type map [, force = false])`

> [!Note]
> Only available on custom `Mime` instances

Define MIME type -> extensions.

Attempting to map a type to an already-defined extension will `throw` unless the `force` argument is set to `true`.

```javascript
@hutechwebsite/animi-sunt-labore-architecto.define({'text/x-abc': ['abc', 'abcd']});

@hutechwebsite/animi-sunt-labore-architecto.getType('abcd');            // ⇨ 'text/x-abc'
@hutechwebsite/animi-sunt-labore-architecto.getExtension('text/x-abc')  // ⇨ 'abc'
```

## Command Line

### Extension -> type

```bash
$ @hutechwebsite/animi-sunt-labore-architecto scripts/jquery.js
text/javascript
```

### Type -> extension

```bash
$ @hutechwebsite/animi-sunt-labore-architecto -r image/jpeg
jpeg
```
