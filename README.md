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

### Inputs

See [Spellchecker CLI](https://github.com/tbroadley/spellchecker-cli) for more details about these inputs.

| Name              | Description                                                                                                                                               | Required? | Default Value                                                                         |
| ----------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------- | --------- | ------------------------------------------------------------------------------------- |
| `files`           | An array of files or globs to spellcheck.                                                                                                                 | false     | `["**/*.txt", "**/*.md"]`                                                             |
| `language`        | The language of the files. See Spellchecker CLI for details about default and available languages.                                                        | false     | `"en-US"`                                                                             |
| `dictionaries`    | An array of files to combine into a personal dictionary.                                                                                                  | false     | `[]`                                                                                  |
| `noGitignore`     | Don't respect ignore files (.gitignore, .ignore, etc).                                                                                                    | false     | `false`                                                                               |
| `ignore`          | An array of regexes. Spelling mistakes that match any of these regexes (after being wrapped with ^ and $) will be ignored.                                | false     | `[]`                                                                                  |
| `plugins`         | An array of retext plugins to use. See Spellchecker CLI for details about available plugins.                                                              | false     | `["spell", "indefinite-article", "repeated-words", "syntax-mentions", "syntax-urls"]` |
| `noSuggestions`   | Do not print suggested replacements for misspelled words. This option will improve Spellchecker CLI's runtime when many errors are detected.              | false     | `false`                                                                               |
| `quiet`           | Do not output anything for files that contain no spelling mistakes.                                                                                       | false     | `false`                                                                               |
| `frontmatterKeys` | An array of frontmatter keys whose values should be spellchecked. By default, no values are spellchecked. Only valid when the frontmatter plugin is used. | false     | `[]`                                                                                  |
| `reports`         | An array of report files to generate. The type of the report is based on the extension of the file. (Supported: .junit.xml and .json)                     | false     |                                                                                       |
| `config`          | A path to a config file.                                                                                                                                  | false     |                                                                                       |

Here's an example that uses inputs:

```yaml
- uses: tbroadley/spellchecker-cli-action@v1
  with:
    files:
      - **/*.md
      - !build/*.md
    quiet: true
```
