# Gulp Tutorial v4.0.2
---

## Contents
---

* Quick Start
* JavaScript and Gulpfiles
* Creating Tasks
* Async Completion
* Working with Files
* Explaining Globs
* Using Plugins
* Watching Files

---

### Quick Start
---

If you've previously installed gulp globally, run `npm rm --global gulp`.

**Check for node, npm, and npx**

`$ node --version`

`$ npm --version`

`$ npx --version`

If they are not installed, follow the instructions on the [Gulp.js](https://gulpjs.com) website. Lookup the Getting Started Section!!

**Install the gulp command line utility**

`$ npm install --global gulp-cli`

**Create a project directory and navigate into it**

`$ npx mkdirp my-project`

`$ cd my-project`

**Create a package.json file in your project directory**

`$ npm init`

This will guide you through giving your project a name, version, description, etc.

**Install the gulp package in your devDependencies**

`$ npm install --save-dev gulp`

**Verify your gulp versions**

`$ gulp --version`

Ensure the output matches the example run below or you might need to restart the steps in this guide.

```
$ gulp --version
CLI version: 2.3.0
Local version: 4.0.2
```

**Create a gulpfile**

Using your text editor, create a file named gulpfile.js in your project root with these contents:

```javascript
const defaultTask = (cb) => {
  // place code for your default task here
  cb();
};

exports.default = defaultTask
```

**Test it**

Run the gulp command in your project directory:

`$ gulp`

To run multiple tasks, you can use `$ gulp <task> <othertask>`.

**Result**

The default task will run and do nothing.

```bash
$ gulp
[20:30:26] Using gulpfile ~/Documents/workbench/gulp_tutorial/gulpfile.js
[20:30:26] Starting 'default'...
[20:30:26] Finished 'default' after 19 ms
```

---

### JavaScript and Gulpfiles
---

Gulp allows you to use existing JavaScript knowledge to write gulfiles
or to use your experience with gulpfiles to write plain JavaScript.
Although a few utilities were provided to simplify working with the
filesystem and commandline, everything else you write is pure JavaScript.

**Gulpfile explained**

A gulpfile is a file in your project directory titled `gulpfile.js`
(or capitalized as `Gulpfile.js`, like Makefile), that automatically
loads when you run the `gulp` command. Within this file, you'll often
see gulp APIs, like `src()`, `dest()`, `series()`, or `parallel()` but
any vanilla JavaScript or Node modules can be used. Any exported functions
will be registered into gulp's task system.

**Transpilation**

You can write a gulpfile using a language that requires transpilation,
like TypeScript or Babel, by changing the extentension on your `gulpfile.js`
to indicate the languge and install the matching transpiler module.

  * For TypeScript, rename to `gulpfile.ts` and install the
    (ts-node)[https://www.npmjs.com/package/ts-node] module.
  * For Babel, rename to `gulpfile.babel.js` and install the
    (@babel/register)[https://www.npmjs.com/package/@babel/register] module.

**Most new versions of node support most features that TypeScript or**
**Babel provide, except the `import` / `export` syntax. When only that syntax**
**is desired, rename to `gulpfile.esm.js` and install the**
**(esm)[https://www.npmjs.com/package/esm] module.**

For a more advanced dive into this topic and the full list of supported
extensions, see our (gulpfile transpilation)[https://gulpjs.com/docs/en/documentation-missing] documentation.

**Splitting a gulpfile**

Many users start by adding all logic to a gulpfile. If it ever grows too
big, it can be refactored into separate files.

Each task can be split into its own file, then imported into your gulpfile
for composition. Not only does this keep things organized, but it allows you to test each task independently or vary composition based on conditions.

Node's module resolution allows you to replace your `gulpfile.js` file
with a directory named `gulpfile.js` that contains an `index.js` file
which is treated as a `gulpfile.js`. This directory could then contain
your individual modules for tasks. If you are using a transpiler, name
the folder and file accordingly.

