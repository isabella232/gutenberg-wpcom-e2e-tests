# Gutenlypso e2e

Manual e2e suite for Gutenberg running in a WPCOM Sandbox.

## Instructions

### Note: These tests will wipe out all posts and comments from the site!

1. Install the dependencies:

```
npm install
```

2. Copy the `config-example.json` file as `config.json` and fill the `sandbox` object with the URL of a WPCOM Sandbox site and the credentials of an editor (or higher role) user.
<br>
To observe the tests visually, set `puppeteer.headless = false` in `config.json`, and increase `puppeteer.slowMo` until the tests are slow enough (I've found `50` to be my sweet spot).

3. Obtain the e2e tests from a Gutenberg release (e.g. [`v4.2.0`]((https://github.com/WordPress/gutenberg/releases/tag/v4.2.0))):

```
npm run update-e2e v4.2.0
```

4. Overwrite the Core e2e with WPCOM specific instructions:

```
npm run overwrite-e2e
```

5. Turn on the Sandbox and...
```
npm run test
```

## Sync with Gutenberg

As of 2018-11-20, this uses [Gutenberg 4.2.0](https://github.com/WordPress/gutenberg/releases/tag/v4.2.0) as it's the version used by the WPCOM Sandbox.

To update it as needed:

1. Run `npm update-e2e` with the tag of a new Gutenberg release (e.g. `npm update-e2e v4.5.0`).

2. Check if there are big changes between `/e2e-overrides` and the new `/e2e` folder, and update the overrides as needed.
<br>
(**IMPORTANT**: keep the same folder structure!)
<br>
E.g. currently, most overrides are in `/support/utils.js`, but in future versions, all the utils functions will be moved into their own files.
3. Run `npm overwrite-e2e` to copy the overrides in the `/e2e` folder.
