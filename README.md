# ESLint Config

Shareable ESLint Configuration to [apply coding standards][using-eslint] across javascript development.

<a href="https://xkcd.com/1513/">
<img
  src="https://imgs.xkcd.com/comics/code_quality.png"
  alt="Code Quality" 
/>
</a>

[using-eslint]: https://medium.com/the-node-js-collection/why-and-how-to-use-eslint-in-your-project-742d0bc61ed7

----
# Getting Started

## Installation

Install peer dependencies and install the eslint configuration:

```bash
npm install --save-dev eslint prettier eslint-plugin-prettier eslint-config-prettier
npm install --save-dev @neozenith/eslint-config
echo "**/node_modules/**" >> .eslintignore
```

## Configuration

### Basic Configuration

Then add the following to your `package.json`:

```json
{
  "eslintConfig":{ "extends": "@neozenith" }
}
```

Well that seems really simple right? And everyone gets the same rules, no excuses.

### Advanced Configuration

In future, environment specific rules, would be specified as below: 

```json
  "eslintConfig":{
    "extends":[
      "@neozenith",
      "@neozenith/eslint-config/node"
    ]
  }
}
```

### Scripts

Finally you'll want to add the following scripts to your `package.json`. 

```json
{

  "scripts": {
    "test:lint:all":"./node_modules/.bin/eslint --ignore-path .",
    "test:lint":"npm run test:lint -- --quiet",
    "test:lint:fix":"npm run test:lint -- --fix",
    "pretest":"npm run test:lint"
  }
}
```

 - `test:lint:all` - this will run `eslint` as per usual outputting all errors and warnings
 - `test:lint` - including the `--quiet` flag reduces `eslint`'s output to errors only
 - `test:lint:fix` - this fixes all errors that are _auto-fixable_ such as formatting issues that do not impact the semantics of the code. All `prettier` rules are always _auto-fixable_.
 - `pretest` - By running this before your tests it will enforce linting and halt on any errors preventing `npm test` from actually running until linting is satisfied. You may want to update this to `test:lint:all` so that it breaks on warnings too. 

----
# Maintaining

```bash
# Bump version number according to changes
npm version [major|minor|patch]

# Publish a public scoped repository
npm publish
```
