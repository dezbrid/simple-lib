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

git commit -m "first commit"