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

---

### JavaScript and Gulpfiles
---


