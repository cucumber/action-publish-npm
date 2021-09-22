# publish-npm

Publishes an NPM module to https://npmjs.com

Needs Node to be installed first.

## Inputs

* `npm-token`
* `working_directory` (default `.`)

## Example

```yaml
name: Publish

on: 
  push:
    branches:
      - "release/*"

jobs:
  publish-ui:
    name: Publish UI package to NPM
    runs-on: ubuntu-latest
    environment: Release
    steps:
      - uses: actions/checkout@v2
      - uses: actions/setup-node@v2
        with:
          node-version: '16'
      - name: Test the action
        uses: cucumber-actions/publish-npm@v1.0.0
        with:
          npm-token: ${{ secrets.NPM_TOKEN }}
          working-directory: "packages/ui"
```
