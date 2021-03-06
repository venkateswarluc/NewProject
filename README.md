# check-code-coverage [![ci status][ci image]][ci url] ![check-code-coverage](https://img.shields.io/badge/code--coverage-100%-brightgreen)
> Utilities for checking the coverage produced by NYC against extra or missing files

## Use

```shell
npm i -D check-code-coverage
# check if .nyc_output/out.json has 100% code coverage for main.js
npx check-coverage main.js
# check if .nyc_output/out.json has files foo.js and bar.js covered and nothing else
npx only-covered foo.js bar.js
```

## only-covered

By default `only-covered` script reads `.nyc_output/out.json` file from the current working directory. You can specify a different file using `--from` parameter

```shell
only-covered --from examples/exclude-files/coverage/coverage-final.json main.js
check-coverage --from examples/exclude-files/coverage/coverage-final.json main.js
```

## check-total

If you generate coverage report using reporter `json-summary`, you can check the total statements percentage

```shell
check-total
# with default options
check-total --from coverage/coverage-summary.json --min 80
```

## update-badge

If your README.md includes Shields.io badge, like this

    ![check-code-coverage](https://img.shields.io/badge/code--coverage-80%-brightgreen)

You can update it using statements covered percentage from `coverage/coverage-summary.json` by running

```shell
update-badge
```

If the coverage summary has 96%, then the above badge would be updated to

    ![check-code-coverage](https://img.shields.io/badge/code--coverage-96%-brightgreen)

Related project: [dependency-version-badge](https://github.com/bahmutov/dependency-version-badge)

The badges will have different colors, depending on the coverage, see [bin/update-badge.js](bin/update-badge.js)

If the code coverage badge is not found, a new badge is inserted on the first line.

## Debug

To see verbose log messages, run with `DEBUG=check-code-coverage` environment variable

[ci image]: https://github.com/bahmutov/check-code-coverage/workflows/ci/badge.svg?branch=master
[ci url]: https://github.com/bahmutov/check-code-coverage/actions
