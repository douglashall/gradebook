[![Build Status](https://api.travis-ci.org/edx/gradebook.svg?branch=master)](https://travis-ci.org/edx/gradebook) [![Coveralls](https://img.shields.io/coveralls/edx/gradebook.svg?branch=master)](https://coveralls.io/github/edx/gradebook)
[![npm_version](https://img.shields.io/npm/v/@edx/gradebook.svg)](@edx/gradebook)
[![npm_downloads](https://img.shields.io/npm/dt/@edx/gradebook.svg)](@edx/gradebook)
[![license](https://img.shields.io/npm/l/@edx/gradebook.svg)](@edx/gradebook)
[![semantic-release](https://img.shields.io/badge/%20%20%F0%9F%93%A6%F0%9F%9A%80-semantic--release-e10079.svg)](https://github.com/semantic-release/semantic-release)

# gradebook

Please tag **@edx/educator-neem** on any PRs or issues.

## Introduction

The front-end of our editable Gradebook feature.

## Usage

To install gradebook into your project:
```
npm i --save @edx/gradebook
```

## Running the UI Standalone

After cloning the repository, run `make up-detached` in the `gradebook` directory - this will build and start the `gradebook` web application in a docker container.

The web application runs on port **1991**, so when you go to `http://localhost:1991` you should see the UI.

If you don't, you can see the log messages for the docker container by executing `make logs` in the `gradebook` directory.

Note that `make up-detached` executes the `npm run start` script which will hot-reload JavaScript and Sass files changes, so you should (:crossed_fingers:) not need to do anything (other than wait) when making changes.

## Directory Structure

* `config`
  * Directory for [`webpack`](https://webpack.js.org/) configurations
* `public`
  * Entry point for the single-page application - `gradebook` has a single `index.html` file
* `src`
  * `components`
    * Directory for presentational `React` components
  * `containers`
    * Directory for container `React` components
  * `data`
    * `actions`
      * Directory for `Redux` action creators
    * `constants`
    * `reducers`
      * Directory for `Redux` reducers
* [`.babelrc`](#babelrc)
* [`.dockerignore`](#dockerignore)
* [`.eslintignore`](#eslintignore)
* [`.eslintrc.js`](#eslintrcjs)
* `.gitignore`
* [`npmignore`](#npmignore)
* [`.travis.yml`](#travisyml)
* `docker-compose.yml`
* `Dockerfile`
* `LICENSE`
* `Makefile`
* `package-lock.json`
* [`package.json`](#packagejson)

### `.babelrc`

We use [`Babel`](https://babeljs.io/) to transpile `ES2015+` JavaScript to `ES5` JavaScript. `ES5` JavaScript has [greater browser compatibility](http://kangax.github.io/compat-table/es5/) than [`ES2015+`](http://kangax.github.io/compat-table/es6/).

The `.babelrc` file is used to specify a particular configuration - for example, we use the [`babel-preset-react`](https://babeljs.io/docs/plugins/preset-react/), which, among other things, allows `babel` to parse `JSX`.

### `.dockerignore`

The important thing to remember is to add the `node_modules` directory to `.dockerignore` - for more information [see the Docker documentation](https://docs.docker.com/engine/reference/builder/#dockerignore-file).

### `.eslintignore`

We use [`eslint`](https://eslint.org/) for our `JavaScript` linting needs. The `.eslintignore` file is used to [specify files or directories to, well, ignore](https://eslint.org/docs/user-guide/configuring#ignoring-files-and-directories).

While `eslint` automatically ignores `node_modules`, we like to add it to the `.eslintignore` just for the added explicitness. In addition, you probably want to add the directory for your compiled files (in our case, `./dist`) and your coverage directory (in our case, `./coverage`).

### `.eslintrc`

This is where the actual `eslint` configuration is specified. All `edX` JavaScript projects should extend either the [`eslint-config-edx`](https://github.com/edx/eslint-config-edx/blob/master/packages/eslint-config-edx/README.md) or [`eslint-config-edx-es5`](https://github.com/edx/eslint-config-edx/blob/master/packages/eslint-config-edx-es5/README.md) configurations (for `ES2015+` and `ES5` JavaScript, respectively). Both configurations can be found in [the `eslint-config-edx` repository](https://github.com/edx/eslint-config-edx).

### `.npmignore`

We are not currently publishing this package to [`npm`](https://www.npmjs.com/). If we did, we would want to exclude certain files from getting uploaded to `npm` (like our coverage files, for example). For more information, see [the `npm` documentation](https://docs.npmjs.com/misc/developers#keeping-files-out-of-your-package).

### `.travis.yml`

We use [`Travis CI`](https://travis-ci.org/) to build (and deploy) our application. The `.travis.yml` file specifies the configuration for `Travis` builds. For more information, see [the `Travis` documentation](https://docs.travis-ci.com/user/customizing-the-build/).

### `package.json`

Arguably, one of the **most important files in an `npm`-based application**, the `package.json` file specifies everything from the `name` of the application, were it to be published to `npm`, to it's `dependencies`.

For more information, see [the `npm` documentation](https://docs.npmjs.com/files/package.json).

## Helpful Applications

### [`Greenkeeper`](https://greenkeeper.io/)

[`Greenkeeper`](https://greenkeeper.io/) is basically a `GitHub` application that handles `npm` dependencies. It will automatically open PRs with `package.json` updates when new versions of your `npm` dependencies get published. There are ways to also automatically keep the `package-lock.json` in-line, in the same PR, using [`greenkeeper-lockfile`].

For more information, see [the `Greenkeeper` documentation](https://greenkeeper.io/docs.html#what-greenkeeper-does).

## Authentication with backend API services

See the [`@edx/frontend-auth`](https://github.com/edx/frontend-auth) repo for information about securing routes in your application that require user authentication.
