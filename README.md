# single-spa demo - Nav

## Overview

This repo is used in conjunction with three other repos listed below. Together they make up an application composed of microfrontends. Each app can be updated and deployed independently of the others.

- **Root Config** (https://github.com/thawkin3/single-spa-demo-root-config)
- **Nav App** (This Repo) (https://github.com/thawkin3/single-spa-demo-nav)
- **Page App 1** (https://github.com/thawkin3/single-spa-demo-page-1)
- **Page App 2** (https://github.com/thawkin3/single-spa-demo-page-2)

## Demo

You can find the demo here: https://thawkin3-single-spa-demo.herokuapp.com/page1

# Article

You can find the whole article here: https://www.freecodecamp.org/news/developing-and-deploying-micro-frontends-with-single-spa/

## How It Works

This project uses [single-spa](https://single-spa.js.org/) to architect an app composed of micrfrontends. In the root config, the three microfrontend apps (nav, page 1, and page 2) are registered with singe-spa. The main `index.ejs` file contains an import map, which references where to find the compiled JavaScript bundle for each microfrontend. [SystemJS](https://github.com/systemjs/systemjs) is the module loader which then loads the bundles when needed.

Each repo is set up with [Travis CI](https://travis-ci.org/) for running jobs as part of a continuous integration pipeline. When new code is pushed to the master branch for any of the repos, the new code is compiled and then uploaded to AWS S3, which serves as a CDN. The CI job also updates the import map file to reference the new bundle for the updated project.

## NPM Scripts

- `analyze`: Analyzes the makeup of the app bundle
- `build`: Creates a production build
- `coverage`: Runs unit tests and generates a coverage report
- `lint`: Lints the code using [ESLint](https://eslint.org/)
- `prettier`: Formats the code using [Prettier](https://prettier.io/)
- `start`: Starts a webpack dev server for running the app in development mode
- `test`: Runs unit tests using [Jest](https://jestjs.io/)
- `watch-tests`: Runs unit tests in "watch" mode
