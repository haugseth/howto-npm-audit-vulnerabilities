# How to fix vulnerabilities in npm packages

After running `npm install lite-server` the installation reported 1 *high* severity vulnerability found in one or more of the dependencies.

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
