# mega-linter-plugin-frontmatter-linter

[![MegaLinter](https://github.com/wesley-dean/mega-linter-plugin-fmlint/actions/workflows/megalinter.yml/badge.svg)](https://github.com/wesley-dean/mega-linter-plugin-fmlint/actions/workflows/megalinter.yml)
[![Dependabot Updates](https://github.com/wesley-dean/mega-linter-plugin-fmlint/actions/workflows/dependabot/dependabot-updates/badge.svg)](https://github.com/wesley-dean/mega-linter-plugin-fmlint/actions/workflows/dependabot/dependabot-updates)
[![Scorecard supply-chain security](https://github.com/wesley-dean/mega-linter-plugin-fmlint/actions/workflows/scorecard.yml/badge.svg)](https://github.com/wesley-dean/mega-linter-plugin-fmlint/actions/workflows/scorecard.yml)

This is a MegaLinter plugin for linting YAML frontmatter found in Markdown
files.

## Introduction

[MegaLinter](https://github.com/oxsecurity/megalinter) by
[OxSecurity](https://github.com/oxsecurity) is a linter tool that supports
various programming languages and file formats. This repository contains a
MegaLinter plugin for linting YAML frontmatter found in Markdown files.
[yamllint](https://github.com/adrienverge/yamllint) by
[adrienverge](https://github.com/adrienverge) is used to perform the actual
linting while [GNU sed](https://www.gnu.org/software/sed/) is used to extract
the frontmatter from the Markdown files.  This plugin is designed to be used
with MegaLinter and is not intended to be used as a standalone tool.

## Usage

To use this plugin, you need to have MegaLinter installed. Please refer to the
[MegaLinter documentation](https://nvuillam.github.io/megalinter/) for
installation instructions.

### MegaLinter Configuration

To use this plugin, add the following to your MegaLinter configuration:

```yaml
PLUGINS:
  - "https://raw.githubusercontent.com/wesley-dean/mega-linter-plugin-fmlint/refs/heads/main/mega-linter-plugin-fmlint/fmlint.megalinter-descriptor.yml
```

> [!TIP]
> Simply adding the plugin to the `PLUGINS` section will cause MegaLiner to read
> the descriptor and make it available for use.  However, depending on your
> MegaLinter configuration, you may need to enable the linter in the
> `ENABLE_LINTERS` section as well.  For example:

```yaml
ENABLE_LINTERS:
  - "MARKDOWN_FMLINT""
```

### Configuring the Linter

To configure `yamllint` (the tool that performs the actual linting), you may
create a `.fmlint.yml` file in the root of your repository. For more
information on configuring, refer to the
[yamllint documentation](https://yamllint.readthedocs.io/en/stable/configuration.html)

> [!NOTE]
> Because `yamllint` is doing the linting, the configuration file must be a
> valid configuration for `yamllint`.  By default, the plugin will look for a
> file named `.fmlint.yml` in the root of your repository.  It will not look for
> a file named `.yamllint.yml` or any other name.  If you want to use a
> different name, you can specify the name of the file in the
> `FMLINT_CONFIG_FILE` option.  This is because one is likely to have a
> different configuration for `yamllint` than for `fmlint`.  If you want to
> use the same configuration for both, you can simply create a symlink to the
> file in the root of your repository.
