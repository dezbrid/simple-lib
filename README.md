# Make a Librery React with TypeScript

## Create

1. create new folder
2. use command yarn init in terminal inside the new folder and answer the question

```bash
yarn init
question name (SimpleLib): simplelib
question version (1.0.0):
question description: example the how create  simple lib
question entry point (index.js):
question repository url:
question author: Dez
question license (MIT):
question private:
success Saved package.json
```

3. install TypeScript

```bash
yarn add -D typescript
```

4. create a new tsconfig.json file

```json
{
  "compilerOptions": {
    "outDir": "lib",
    "module": "esnext",
    "target": "es5",
    "lib": ["es6", "dom", "es2016", "es2017"],
    "jsx": "react",
    "declaration": true,
    "moduleResolution": "node",
    "esModuleInterop": true,
    "strictNullChecks": false,
    "allowSyntheticDefaultImports": true,
    "esModuleInterop": true,
    "baseUrl": "./",
    "paths": {
      "@": ["src/"]
    },
    "plugins": [
      {
        "transform": "typescript-transform-paths"
      },
      {
        "transform": "typescript-transform-paths",
        "afterDeclarations": true
      }
    ]
  },
  "include": ["src"],
  "exclude": ["node_modules", "lib"]
}
```

5. install react, react-dom, and types

```bash
yarn add -D react-dom react @types/react-dom @types/react
```

6. in packege.json add peerDependencies

```json
"peerDependencies": {
    "react": "^16.8.0",
    "react-dom": "^16.8.0"
 }
```

## Build

1. in the package.json

```json
"scripts": {
    "build": "rm -rf ./lib && yarn build:esm && yarn build:cjs ",
    "build:esm": "tsc",
    "build:cjs": "tsc --module commonjs --outDir lib/cjs",
 },
 "main": "./lib/cjs/index.js",
  "module": "./lib/index.js",
  "types": "./lib/index.d.ts",
"files": [
    "/lib"
 ]
```

2. run

```bash
yarn build
```

## Publish in your Git
### Prerequisites
1. We need to generate a [personal access token](https://github.com/settings/tokens/new) on Github in your account with  `  write:packages and  read:packages` permissions. Make sure to copy your new personal access token now. You won’t be able to see it again! For more information, you can check [Github documentation](https://docs.github.com/en/github/authenticating-to-github/creating-a-personal-access-token).
 2. Then, create .npmrc file in your root proyect: 
```txt
  //npm.pkg.github.com/:_authToken=TOKEN
 @USER_GITHUB:registry=https://npm.pkg.github.com/
 
 ```
---
Don't commit the changes to this file!
---

1. add in package.json

```json
"publishConfig": {
    "registry": "https://npm.pkg.github.com"
  },
  "scripts": {
    "login": "npm login --scope=@your_user_github --registry=https://npm.pkg.github.com"
  }
```
2. login in terminal  with npm
```bash
npm login
Username: 
```

## Publish in yarn or npm

### Prerequisites

create account in  [npmjs](https://www.npmjs.com/signup)

1. login in terminal use yarn or npm

```bash
yarn login
question npm username: "your username"
question npm email: "your email"
```

2. publish in yarn
