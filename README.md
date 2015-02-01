
# Module Style Guide

## Files

#### `LICENSE`

Always create a separate file for your license.
Main reason is that no one will complain about not having a license.

#### `README.md`

Readme's are important!

In general, every readme should have, in order:

- Description including:
  - Purpose
  - Scope
  - Features
  - Limitations
- Resources including:
  - Forums and chat
  - Wikis
  - Examples
  - Maintainers and collaborators
- Code Examples including:
  - Installation
  - Quick start guide
- API documentation
- License

Don't bother including:

- List of all contributors - you can check GitHub for that.

#### `package.json`

Be sure to include in your `package.json`:

- `.repository` - if you don't set this, you suck.
- `.files` - a whitelist of files to include.
  The latest version of npm automatically always bundles the readme, changelogs, and licenses,
  so there's no need to add those files.
  The only time you don't use this is when having a `.npmignore` is easier, which is rare for simple modules.
- `.browser` - see [browser field spec for package.json](https://gist.github.com/defunctzombie/4339901)
- `.main` - only if not `index.js`

## Folders

### `lib/`

If your module uses more than one file,
put all the files in `lib/` and create a `lib/index.js` file.
Then set `.main = 'lib'` in your `package.json`.

### `src/`

`src/` is the equivalent to `lib/`,
except it's for code that needs to be compiled.

### `bin/`

Put all your executables in the `bin/` folder.
Executables should not have any extensions.

Then, set these binaries in your `package.json`:

```json
{
  "bin": {
    "run-this-server": "bin/www"
  }
}
```

If you `npm link` or install this module globally,
then `run-this-server` will be a global command!

### `test/`

Put all your tests in this folder.
For some reason, some test runners don't support `tests/` as a folder.

## Scripts

### `npm test`

Running `npm test` should always run all the tests.

### `npm start`

If this module is a server or an app,
then running `npm start` should start the server,
at least for development.

## Entry points

Always define `.main`.
Generally, your entry points should either be:

- `index.js` by default
- `lib/`
- A top level file with the same name as your repository
