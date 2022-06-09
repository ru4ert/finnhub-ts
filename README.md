# Finnhub-ts

Why? There is an existing one [finnhub-js](https://github.com/Finnhub-Stock-API/finnhub-js)

> Because it's not working in every enviroment

## Source

Swagger file:
[swagger.json](https://finnhub.io/static/swagger.json)

OpenAPI Client:
[openapi-generator-cli.jar](https://github.com/OpenAPITools/openapi-generator)

How generate new version:

1. `java -jar .\openapi-generator-cli.jar generate -i .\swagger.json -o .\ -g typescript-axios --skip-validate-spec -c .\openapi-generator.json`
2. update npm version
3. push to npm

## finnhub-ts@1.0.0

This generator creates TypeScript/JavaScript client that utilizes [axios](https://github.com/axios/axios). The generated Node module can be used in the following environments:

Environment

- Node.js
- Webpack
- Browserify

Language level

- ES5 - you must have a Promises/A+ library installed
- ES6

Module system

- CommonJS
- ES6 module system

It can be used in both TypeScript and JavaScript. In TypeScript, the definition should be automatically resolved via `package.json`. ([Reference](http://www.typescriptlang.org/docs/handbook/typings-for-npm-packages.html))

## Usage for 3rd party apps:

## Developing:

### Building

To build and compile the typescript sources to javascript use:

```
npm install
npm run build
```

### Publishing

First build the package then run `npm publish`

### Consuming

navigate to the folder of your consuming project and run one of the following commands.

_published:_

```
npm install finnhub-ts@1.0.0 --save
```

_unPublished (not recommended):_

```
npm install PATH_TO_GENERATED_PACKAGE --save
elp -g typescript-axios
```
