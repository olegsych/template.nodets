## Pre-requisites
- [Node](https://nodejs.org/en/download)
- [VS Code](https://code.visualstudio.com/Download)

## Create
```
npm init --force
npm install typescript --save-dev
npm install typings --save-dev
.\node_modules\.bin\typings install dt~node --global --save
```

Create or update:
- `tsconfig.json` allows running `tsc` to build all TypeScript files.
- `package.json` contains npm module dependencies and scripts.
- `typings.json` contains TypeScript typing definition dependencies.
- `.gitignore` prevents Git from storing intermediate files produced by build.
- `.vscode/tasks.json` define VS Code `build` task.
- `.vscode/launch.json` defines VS Code `launch` task.
- `src\program.ts` is the application entry point.

## Clone
```
git clone https://github.com/olegsych/template.nodets.git
cd template.nodets
npm install
```

How it works:
- The `npm install` command installs module dependencies and runs the `install` script defined in the `package.json`.
- The `install` script invokes runs the `typings install` command from the `typings` module restored by `npm`.
- The `typings install` command installs TypeScript definitions defined in the `typings.json`.

## Build
- VS Code: `Ctrl+Shift+B`
- Shell: `npm run build`

How it works: 
- `npm` runs the `build` script defined in `package.json` to invoke the `tsc` command from the `typescript` module.
- `tsc` looks for `tsconfig.json` in the current directory and uses
  - `outDir` property to make `tsc` generate `.js` files in the `build` subfolder,
  - `sourceMaps` to generate `.js.map` along with them.

## Run
Shell: `node build/program.js`

How it works:
- `tsc` compiles `src/program.ts` to `build/program.js` based on the `tsconfig.json` settings
- `node` runs the JavaScript in `index.js`

## Debug 
VS Code: `F5`

How it works:
- `.vsconfig/launch.json` defines `Launch` configuration
  - `program` property to indicate which `.ts` file contains the application entry point,
  - `sourceMaps` property to make debugger use `.js.map` files,
  - `outDir` property to specify where to find them.
