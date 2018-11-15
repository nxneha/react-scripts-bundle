# react-scripts

Customized [`react-scripts`](https://github.com/facebook/create-react-app/tree/master/packages/react-scripts) for Nuage Networks VSD UI Framework

## Getting Started

Clone the repository to make changes:

```
git clone https://github.com/nxneha/react-scripts.git
```

### Prerequisites

This library is meant for use in an un-ejected CRA app. (See [facebook/create-react-app](https://github.com/facebook/create-react-app).) It sligthly modifies the behavior of the original scripts used to run, build and test the CRA app.

### Installation

To install this customized version of `react-scripts`, simply point the corresponding `package.json` key towards this github repo.

i.e. Replace this:

```json
"react-scripts": "^2.1.1"
```

with:

```json
"react-scripts": "nxneha/react-scripts"
```

Then, in your project directory, run npm install command:

```
npm i
```

Your project should now be using the custom version of `react-scripts`.

### Usage

The usage is identical to original package. The available npm scripts are:

```json
"scripts": {
  "start": "react-scripts start",
  "build": "react-scripts build",
  "test": "react-scripts test",
  "eject": "react-scripts eject",
},
```

## Customization

_**Current version: [2.1.1](https://github.com/facebook/create-react-app/tree/v2.1.1/packages/react-scripts)**_

The following customization has been done to the original `react-scripts` package.

#### `scripts/start.js`

##### Disable typescript checking

Typescript checking can be disabled until the project is updated to React 16.

Remove or comment out these lines of code:

```javascript
30    const verifyTypeScriptSetup = require('./utils/verifyTypeScriptSetup');
31    verifyTypeScriptSetup();
```

#### `script/utils/createJestConfig.js`

#####

TODO

## Built with

This package includes scripts and configuration used by [Create React App](https://github.com/facebook/create-react-app).<br>
Please refer to its documentation:

- [Getting Started](https://github.com/facebook/create-react-app/blob/master/README.md#getting-started) – How to create a new app.
- [User Guide](https://github.com/facebook/create-react-app/blob/master/packages/react-scripts/template/README.md) – How to develop apps bootstrapped with Create React App.
- [`react-scripts`](https://github.com/facebook/create-react-app/tree/v2.1.1/packages/react-scripts) – Original source code used at **v2.1.1**.

## Versioning

This library follows the same versioning as facebook's `react-scripts` package.

At the time of writing this, `react-scripts` version was [2.1.1](https://github.com/facebook/create-react-app/tree/v2.1.1/packages/react-scripts), which is the original source used.

## License

This project is licensed under the MIT License - see the [LICENSE.md](LICENSE.md) file for details
