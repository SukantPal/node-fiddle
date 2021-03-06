<h2 align="center">
[@pixi-build-tools/]fiddle
</h2>

<p align="center">
    <span>
        <img alt="npm (tag)" src="https://img.shields.io/npm/v/@pixi-build-tools/fiddle/latest">
        &#8287;
        <img alt="David" src="https://img.shields.io/david/sukantpal/pixi-fiddle">
        &#8287;
        <img alt="npm collaborators" src="https://img.shields.io/npm/collaborators/@pixi-build-tools/fiddle">
    </span>
</p>

<p align="center">
PixiJS + webpack + Babel + @pixi/eslint-config
</p>

This package spun off of @alkamin's pixijs-template repo. I have tuned this for local development of PixiJS
so that **you can test your changes to pixi.js-related packages locally**.

The use of ECMAScript allows you to copy/paste your fiddle to online JavaScript editors like CodePen.

## Usage

Clone the repository and create your first fiddle:

1) `git clone https://github.com/SukantPal/pixi-fiddle`
2) `npm run open -- --fiddle basic-fiddle`
3) `npm run start`

The entry point is `src/index.js`. This will be initialized with some boilerplate code.

Your fiddles are stored in the `fiddle-workspace` directory. This package helps you copy fiddles from and to the source directory `src`.

## Features

* Creating and switching between different fiddles

* Bundling up JavaScript & GLSL files into one fiddle file

* Importing JSFiddles with one command

## Commands

<ul>
    <li><code>open</code>: <code>npm run open -- --fiddle my-fiddle</code>

This will save the current fiddle and "open" the fiddle passed via <code>--fiddle</code>. Opening a fiddle just copies its contents into the source directory

You can pass a <code>--no-save</code> option to "forget" the current fiddle state.

**This is also the current way to create a new fiddle!**

<li><code>flush</code>: <code>npm run flush</code>

This will save the current fiddle. You can use this before you start tearing down stuff in your fiddle for refactoring/restructuring something big!

<li><code>delete</code>: <code>npm run delete my-fiddle</code>

This is used to delete the fiddle saved in `fiddle-workspace`. It will not reset the source directory contents.

<li><code>pwf</code>: <code>npm run pwf</code>
    
This will "print working fiddle" or the fiddle that is currently opened in <code>src</code>.

<li><code>revise</code>: <code>npm run revise</code>
    
This will change the version suffix of your fiddle name. You can use this before flushing your fiddle to keep a "history" of your changes. If the current fiddle is <code>my-fiddle</code>, then it will become <code>my-fiddle-1</code>.

<li><code>export</code>: <code>npm run export</code>
    
This will rollup all JS files in your `src` directory using RollupJS. It also "tries" to erase any local requires to packages given in `pkgWatch` (config file). The resulting fiddle is placed in the `export` directory.

<li><code>import</code>: <code>npm run import $url$ </code>
    
This will download the JSFiddle <code>$url$</code> and extract the JavaScript into `index.js` (and save the file `index.html`). This saves the current fiddle before overwriting the `src` directory.

</ul>

## Config File

You can create a config file `fiddle.config.json` to register your local PixiJS repo. For example,

```json
{
    "pkgWatch": {
        "pixi.js": "../pixi.js/bundles/pixi.js/lib/pixi"
    }
}
```

Make sure path is to the CommonJS bundle (not the project root). Support for adding more packages will be
added.

## Template

If you want to change what code new fiddles have, change the tools/template folder and update `template.registrar.json`
with the files you want "processed".

### Assets

All assets are placed in the `src/assets/` directory and will be available to the app at `assets/`.

### Scripts

* `npm run start` - start the development server
* `npm run build` - build a deployable bundle
* `npm run reinit` - after cloning the repo, run this command to re-initialize the repository for your own project
