# Spellchecker CLI Action

Run [Spellchecker CLI](https://github.com/tbroadley/spellchecker-cli) in GitHub Actions workflows.

## Usage

Here is an example workflow definition that uses `actions/checkout` and this repository:

```yaml
on: push
jobs:
  spellcheck:
    runs-on: ubuntu-latest
    name: Spellcheck
    steps:
      - uses: actions/checkout@v3
      - uses: tbroadley/spellchecker-cli-action@v1
```
