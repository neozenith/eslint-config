# ESLint Config

Shareable ESLint Configuration

----
# Getting Started

Install peer dependencies

```bash
npm install --save-dev eslint prettier eslint-plugin-prettier eslint-config-prettier
```

Install the eslint configuration:

```bash
npm install --save-dev @neozenith/eslint-config
```

Then add the following to your `package.json`:


```json
{
	"scripts": {
		"pretest":"npm run test:lint:fix",
		"test:lint":"./node_modules/.bin/eslint src/*.js test/*.js lib/*.js",
		"test:lint:fix":"./node_modules/.bin/eslint --fix src/*.js test/*.js lib/*.js"
	},

	"eslintConfig":{
		"extends":"@neozenith"
	}
}
```



----
# Maintaining

```bash
# Bump version number according to changes
npm version [major|minor|patch]

# Publish a public scoped repository
npm publish --access public
```
