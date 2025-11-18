[![add-on registry](https://img.shields.io/badge/DDEV-Add--on_Registry-blue)](https://addons.ddev.com)
[![tests](https://github.com/stasadev/ddev-nvm/actions/workflows/tests.yml/badge.svg?branch=main)](https://github.com/stasadev/ddev-nvm/actions/workflows/tests.yml?query=branch%3Amain)
[![last commit](https://img.shields.io/github/last-commit/stasadev/ddev-nvm)](https://github.com/stasadev/ddev-nvm/commits)
[![release](https://img.shields.io/github/v/release/stasadev/ddev-nvm)](https://github.com/stasadev/ddev-nvm/releases/latest)

# DDEV NVM

> [!NOTE]
> Since DDEV v1.25.0+, `nvm` is no longer included by default. Using `ddev nvm install` can make it unclear how to return to the version defined by `nodejs_version`. The switch back is:
>
> ```bash
> ddev nvm alias default system
> ```
>
> And `ddev nvm use` doesn't behave like the interactive `nvm use`, because `nvm` is a shell function rather than a standalone executable and cannot modify the shell environment inside DDEV.
>
> For most projects, [`nodejs_version`](https://docs.ddev.com/en/stable/users/configuration/config/#nodejs_version) offers a more predictable workflow:
>
> ```bash
> ddev config --nodejs-version=20
> ```
>
> It also supports `.nvmrc` with:
>
> ```bash
> ddev config --nodejs-version=auto
> ```

## Overview

This add-on integrates [NVM](https://github.com/nvm-sh/nvm) into your [DDEV](https://ddev.com/) project.

## Installation

```bash
ddev add-on get stasadev/ddev-nvm
ddev restart
```

After installation, make sure to commit the `.ddev` directory to version control.

## Uninstallation

```bash
ddev add-on remove nvm
ddev restart
# Optionally remove cached nvm data
ddev exec 'rm -rf /mnt/ddev-global-cache/nvm_dir/$HOSTNAME'
```

After uninstallation, make sure to commit the `.ddev` directory to version control.

## Usage

> [!TIP]
> You can use NVM inside DDEV [hooks](https://docs.ddev.com/en/stable/users/configuration/hooks/):
>
> ```yaml
> # .ddev/config.yaml
> hooks:
>   post-start:
>     - exec: "nvm install 18 && nvm alias default 18"
> ```

List installed Node.js versions:

```bash
ddev nvm ls
```

List Node.js versions available for installation:

```bash
ddev nvm ls-remote
```

Install a Node.js version and make it the default:

```bash
ddev nvm install 20
ddev nvm alias default 20
```

> [!WARNING]
> Don't use `ddev nvm use <version>` as it won't work as expected due to `nvm` being a shell function.
> Instead, use `ddev nvm alias default <version>` to set the default version.

Check the active Node.js version:

```bash
ddev nvm current
ddev exec node --version
```

Install latest `npm` version:

```bash
ddev nvm install-latest-npm
ddev npm --version
```

Switch between installed versions:

```bash
ddev nvm install 20
ddev nvm install 18
ddev nvm alias default 20
ddev nvm alias default 18
```

To stop using Node.js installed via NVM:

```bash
ddev nvm alias default system
```

## Credits

**Contributed and maintained by [@stasadev](https://github.com/stasadev)**
