# conventional-changelog-project

Commits that follow a standard and descriptive format can be parsed programmitically to learn much about the state of the repository.

Most particularly...

- The next logical **Semantic Version** bump
- **CHANGLOG** (for Humans)

(i.e. Releases)

While many commit formats exist and you can invent your own, this project templates (and examplifies) the most popular, **Conventional** format.

https://github.com/conventional-changelog/conventional-changelog

## How It Works

All tooling is provided via `npm` packages.

### Commits are Linted

In order for any of this to be worthwhile and work, commits have to consistently follow the desired, Conventional, format. Therefore, a pre-commit hook linter in order.

`package.json`
```json
{
  "devDependencies": {
    "@commitlint/cli": "^7.3.2",
    "@commitlint/config-conventional": "^7.3.1",
    "husky": "^1.3.1"
  },
  "husky": {
    "hooks": {
      "commit-msg": "commitlint -E HUSKY_GIT_PARAMS"
    }
  }
}
```
`commitlint.config.js`
```js
module.exports = {extends: ['@commitlint/config-conventional']};
```

https://marionebl.github.io/commitlint/#/guides-local-setup

### Commits are Assisted

Writing repetitive, descriptive commits is necessary for honoring the standard, Conventional, format. However, writing (let alone, learning) them *completely manually* is tiresome and *not* necessary.

Instead of using `git commit`, use...

```bash
> npm run cm
```

`package.json`
```json
{
  "scripts": {
    "cm": "git-cz"
  },
  "devDependencies": {
    "commitizen": "^3.0.5",
    "cz-conventional-changelog": "^2.1.0",
  },
  "config": {
    "commitizen": {
      "path": "./node_modules/cz-conventional-changelog"
    }
  }
}
```

https://github.com/commitizen/cz-cli

### Versioning is Scripted

Once you have a Conventional commit log, you are ready to enjoy auto-generated Changelog and Version bumps.

```bash
> npm run release
```

`package.json`
```json
{
  "scripts": {
    "release": "standard-version"
  },
  "devDependencies": {
    "standard-version": "^4.4.0"
  }
```

https://github.com/conventional-changelog/standard-version