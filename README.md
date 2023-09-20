This is how this repo was set up

## Initialise next-app

```bash
yarn create next-app template-next
```

## Update `tsconfig.json`

```json
{
  "compilerOptions": {
    "target": "es6", // upgrade from es5 to es6
    "allowUnreachableCode": false, // add => raises compiler errors about unreachable code
    "allowUnusedLabels": false, // add =>  raises compiler errors about unused labels
    "noFallthroughCasesInSwitch": true, // add => Ensures that any non-empty case inside a switch statement includes either break or return
    "noImplicitReturns": true, // add => Check all code paths in a function to ensure they return a value.
    "sourceMap": true, // add => Enables the generation of sourcemap files. Easier to debug
    "lib": ["dom", "dom.iterable", "esnext"],
    "allowJs": true,
    "skipLibCheck": true,
    "forceConsistentCasingInFileNames": true,
    "strict": true,
    "noEmit": true,
    "esModuleInterop": true,
    "module": "esnext",
    "moduleResolution": "node",
    "resolveJsonModule": true,
    "isolatedModules": true,
    "jsx": "preserve",
    "incremental": true,
    "paths": {
      "@/*": ["./src/*"]
    },
    "plugins": [
      {
        "name": "next"
      }
    ]
  },
  "include": ["next-env.d.ts", "**/*.ts", "**/*.tsx", ".next/types/**/*.ts"],
  "exclude": ["node_modules"]
}
```

## ESLint and Prettier

```bash
yarn add --dev eslint
```

```bash
yarn add --dev prettier
```

```bash
# To avoid format conflicts between ESLint and Prettierr.
# It turns off all ESLint rules that are unnecessary or might conflict with Prettier.
yarn add --dev eslint-config-prettier
```

```bash
yarn add --dev eslint-config-next
```

### `.eslintrc.json` config

```bash
npx eslint --init
```

### Add the following in `.eslintrc.json`

```json
"rules": {
    "react/react-in-jsx-scope": "off",
    "react/jsx-uses-react": "off"
  }
```

### To make Prettier cooperate with ESLint; add "prettier" to the extends array in your eslintrc.js file.

### Create `.prettierrc`

```json
{
  "semi": true,
  "singleQuote": true,
  "trailingComma": "all",
  "printWidth": 80
}
```

### Create `.prettierignore` and `.eslintignore`

```
.next
next-env.d.ts
node_modules
yarn.lock
package-lock.json
public
```

## Install Husky

```bash
yarn add husky --dev
```

### husky config

```bash
npx husky-init
```

### Update `package.json`

```json
"scripts": {
    "dev": "next dev",
    "build": "next build",
    "start": "next start",
    "check-types": "tsc --pretty --noEmit",
    "check-format": "prettier --check .",
    "check-lint": "eslint . --ext ts --ext tsx --ext js",
    "format": "prettier --write .",
    "test-all": "yarn check-format && yarn check-lint && yarn check-types && yarn build",
    "prepare": "husky install"
  },
```

### Editing the `pre-commit` hook

[link](https://github.com/jarrodwatts/code-like-google/blob/main/.husky/pre-commit) and change `npm run` to `yarn`

## Check out commitlint after this

[Link](https://www.npmjs.com/package/@commitlint/cli)