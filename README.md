# `elm-asset-webpack-loader`

Webpack loader for assets (like images or fonts) in Elm programming language

## Usage

```elm
img [ src "require:src/assets/logo.svg" ] []
```

## Webpack

* This loader is meant to be run in combination with [`elm-webpack-loader`](https://github.com/elm-community/elm-webpack-loader)
* The configuration isn't allowed to have `noParse` for elm files

```js
{
  test: /\.elm$/,
  use: [
    {
      loader: require.resolve("elm-asset-webpack-loader")
    },
    {
      loader: require.resolve("elm-webpack-loader")
    }
  ]
}
```

With this configuration other loaders (like this `svg` example) can be used:

```js
```javascript
{
  test: /\.svg$/,
  loader: require.resolve("file-loader"),
  options: {
    name: "static/media/[name].[hash:8].[ext]"
  }
}
```

## Goals

### Path safety

The build should fail at compile time if an asset path is used, that isn't existing or misspelled.

### Webpack loaders

With this approach any webpack loader can be used. Use cases can be to hash file names, to optimize images and more. See [awesome-webpack#loaders](https://github.com/webpack-contrib/awesome-webpack#loaders).

## Other approaches

* [`elm-assets-loader`](https://github.com/NoRedInk/elm-assets-loader) is a comparable approach, and is probably more sophisticated. The package is marked as deprecated.
* It's possible to require files in JavaScript and pass them as flags to Elm.
