# @kyleshockey/mocha-webpack

`@kyleshockey/mocha-webpack` is a fork of [mocha-webpack](https://github.com/zinserjan/mocha-webpack). Here's what you should know:

* Our first version is `1.1.0`, which is identical to `mocha-webpack@1.1.0`.
* `mocha-webpack`'s 2.x development when it was abandoned was published as `@kyleshockey/mocha-webpack@2.0.0`.<br><br>
* We consider changes in supported mocha/webpack versions to be breaking changes.
    * Our 1.x series will never drop support for Webpack 2/3 or Mocha 4/5
* Our 1.x series is in maintenance, but will still receive security updates.
    * (this fork was initially created to address [CVE-2018-20834](https://nvd.nist.gov/vuln/detail/CVE-2018-20834))

---

> mocha test runner with integrated webpack precompiler

mocha-webpack is basically a wrapper around the following command...
```bash
$ webpack test.js output.js && mocha output.js
```

... but in a much more *powerful* & *optimized* way.

![CLI](./docs/media/cli-test-success.png)

mocha-webpack ...
- precompiles your test files automatically with webpack before executing tests
- handles source-maps automatically for you
- does not write any files to disk
- understands globs & all other stuff as test entries like mocha

Benefits over plain mocha
- has nearly the same CLI as mocha
- you don't rely on hacky solutions to mock all benefits from webpack, like path resolution
- mocha-webpack provides a much better watch mode than mocha

## Watch mode (`--watch`)

Unlike mocha, mocha-webpack analyzes your dependency graph and run only those test files that were affected by this file change.

You'll get continuous feedback whenever you make changes as all tests that are related in any way to this change will be tested again. Isn't that awesome?

If any build errors happens, they will be shown like below

![CLI](./docs/media/cli-compile-failed.png)

## Which version works with mocha-webpack?

#### 2.0
- `webpack@^4`
- `mocha@^4` and `mocha@^5`

#### 1.0
- `webpack@^2` & `webpack@^3`
- `mocha@^2`, `mocha@^3`, `mocha@^4`, and `mocha@^5`

## Installation

Install mocha-webpack via npm install
```bash
$ npm install webpack mocha mocha-webpack --save-dev
```

and use it via npm scripts in your `package.json`

Further installation and configuration instructions can be found in the [installation chapter](./docs/installation/setup.md).

## Sample commands

run a single test

```bash
mocha-webpack simple.test.js
```

run all tests by glob

```bash
mocha-webpack "test/**/*.js"
```
**Note:** You may noticed the quotes around the glob pattern. That's unfortunately necessary as most terminals will resolve globs automatically.

run all tests in directory "test" matching the file pattern *.test.js  (add `--recursive` to include subdirectories)

```bash
mocha-webpack --glob "*.test.js" test
```

Watch mode? just add `--watch`

```
mocha-webpack --watch test
```

### License

MIT