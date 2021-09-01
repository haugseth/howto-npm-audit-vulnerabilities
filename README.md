# How to fix vulnerabilities in npm packages

## Changelog
- 20210901 - Updated with advice from Stack Overflow, first do a sanity check (source at end of document)

## Description
After running `npm install lite-server` the installation reported 1 *high* severity vulnerability found in one or more of the dependencies.

## Sanity check
- Do a sanity check
- In case it's a real problem, check the repository of vulnerable package for existing issues and PRs
- In case there's none, submit an issue
- Fork a repository or use use existing PR as git dependency until it's fixed in NPM release
- In case of nested dependencies, do this at several levels of nesting
- Most times it's expected that you won't advance beyond a sanity check.

## Simple fix
```bash
$ npm audit fix
```

## Manual fix
When running a simple `npm audit fix` doesn't work, and there are still vulnerabilites, add this to your `package.json`, where packagename is the package with the vulnerability, and ^0.0.0 is the version suggested by the npm audit tool.

```json
  "resolutions": {
    "packagename": "^0.0.0"
  }
```

After this, run the following command to fix the dependency.

```bash
$ npx npm-force-resolutions
```

The vulnerability should be fixed!

## Source
- [StackOverflow @Estus Flask](https://stackoverflow.com/users/3731501/estus-flask)
- [How to fix npm vulnerabilities manually](https://stackoverflow.com/questions/51377148/how-to-fix-npm-vulnerabilities-manually)
