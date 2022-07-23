# Spellchecker CLI Action

Run [Spellchecker CLI](https://github.com/tbroadley/spellchecker-cli) in GitHub Actions workflows.

## Use Case

Catch spelling mistakes in your open-source software project's documentation as part of its continuous integration process.

## Usage

Here is an example workflow definition. It uses `actions/checkout` to check out your repository's code, then `tbroadley/spellchecker-cli-action` to spellcheck it.

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
