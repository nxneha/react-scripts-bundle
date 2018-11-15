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

#### `package.json`

Add the following packages to the manifest file:

```json
    "base64-inline-loader": "^1.1.0",
```

#### `config/webpack.config.dev` and `config/webpack.config.prod`

##### base64-inline-loader

Add this loader at the top of the config objects, right under `oneOf` key. Make sure it is present before `url-loader` settings.

```javascript
oneOf: [
  // "base64-inline-loader" converts matching images to base64 strings.
  // If you add this loader at the top, you can leave the "url-loader"
  // as it is, since webpack will use the first loader it matches.
  {
    test: /\.(jpe?g|png|gif|svg)$/i,
    loader: require.resolve('base64-inline-loader'),
    options: {
      name: 'static/media/[name].[hash:8].[ext]',
    }
  },
  // [... "url-loader" settings and so on ...]
]
```

Keeping this loader at the top means that if an image file matches its test, it will be converted to base64 string as intented. The remaining loaders will not be checked, so `url-loader` will not be used for the matching file.

#### `scripts/start.js`

##### Disable typescript checking

Typescript checking can be disabled until the project is updated to React 16.

Remove or comment out these lines of code:

```javascript
30    const verifyTypeScriptSetup = require('./utils/verifyTypeScriptSetup');
31    verifyTypeScriptSetup();
```

#### `script/utils/createJestConfig.js`

Modify the `config` object in this file as follows:

##### Ignore transform

Replace the `transformIgnorePatterns` key:

```json
transformIgnorePatterns: [
  "<rootDir>/node_modules/(?!@)",
  "<rootDir>/src/node_modules/(?!@)"
],
```

##### moduleNameMapper

Add the third key to `moduleNameMapper`:

```javascript
moduleNameMapper: {
  '^react-native$': 'react-native-web',
  '^.+\\.module\\.(css|sass|scss)$': 'identity-obj-proxy',
  "\\.(css|less|scss|sass)$": "identity-obj-proxy"
},
```

##### Ignore files

Add the following object to `config`:

```json
testPathIgnorePatterns: [
  "<rootDir>[/\\\\](build|docs|node_modules|scripts)[/\\\\]",
  "<rootDir>/src/lib/models",
  "<rootDir>/src/lib/vspk",
  "<rootDir>/src/lib/vis-graphs",
  "<rootDir>/src/lib/test-utils",
  "<rootDir>/src/lib/service",
],
```

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
