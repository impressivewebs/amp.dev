# amp.dev

[![Build Status](https://travis-ci.org/ampproject/docs.svg?branch=future)](https://travis-ci.org/ampproject/docs)

This repository is meant to work towards the relaunch of the official website
of [ampproject.org](https://www.ampproject.org/) until we reach a progress
that makes a merge over to the original repository beneficial.

## Requirements

1.  Install the LTS version of [NodeJS](https://nodejs.org). An easy way to do so is with `nvm`. (Mac and Linux: [here](https://github.com/creationix/nvm), Windows: [here](https://github.com/coreybutler/nvm-windows))
    ```sh
    $ nvm install --lts
    ```

1.  Install [Grow](http://grow.io) the static site generator used to build amp.dev:
    ```sh
    $ curl https://install.grow.io | bash
    ```

1.  Install the dependencies for the project:
    ```sh
    $ npm install
    ```

## Develop
If it's your first time working on amp.dev it is recommended to bootstrap your local environment. To do so make sure you have setup a valid [GitHub access token](https://github.com/settings/tokens) in an environment variable named `AMP_DOC_TOKEN` like:

```sh
$ export AMP_DOC_TOKEN="c59f6..."
```

This enables the import from GitHub to run flawlessly which can be started by the following command which additionally will build the Playground and Boilerplate Generator once:

```sh
$ gulp bootstrap
```

You can then start developing in your local environment with the command below. The task will take care of building and copying all files, watching them for changes and rebuild them when needed. Beware that changes to the [express.js](https://expressjs.com/) backend require to restart the task.

```sh
$ gulp develop
```

### Maintenance

#### Documents
Made changes to a lot of Grow documents at once and not quite sure if all references are still valid? You can run `npm run lint:grow` to pick up broken ones.

Also see MAINTENANCE.md for a more detailed explanation of the various frontmatter keys used throughout the project.

#### Samples
Building the samples creates a lot of individual files per sample. In order to still have a quick startup time for development only changed samples are rebuilt. To freshly build *all* samples you can run `npm run develop -- --clean-samples`.

### Run a test build
To run a local test build that does all the minifying and vends the static pages instead of
proxying them through to Grow you can run

```sh
$ gulp fullBuild --env local
$ npm run start:local
```

## Build
Prior running a build it is recommended to run `gulp clean` to ensure your environment doesn't contain any remainings of previous builds - additionally check your working copy for eventual unintended local changes.

To perform a build run the following command with `--env` being one of the following valid environments: `development`, `local`, `staging` or `production`:

```sh
$ gulp fullBuild --env <environment>
```

This builds all parts of the project and might take a while. Usually all builds on amp-dev-staging.appspot.com and amp.dev are built using [Travis CI](https://travis-ci.org/ampproject/docs). In case you want to reproduce one of those remote builds in your local environment you can fetch the built artifacts by running:

```sh
$ gulp fetchArtifacts --travis-build <build_number>
```

- - -

 Copyright 2019 The AMP HTML Authors. All Rights Reserved.

 Licensed under the Apache License, Version 2.0 (the "License");
 you may not use this file except in compliance with the License.
 You may obtain a copy of the License at

      http://www.apache.org/licenses/LICENSE-2.0

 Unless required by applicable law or agreed to in writing, software
 distributed under the License is distributed on an "AS-IS" BASIS,
 WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
 See the License for the specific language governing permissions and
 limitations under the License.
