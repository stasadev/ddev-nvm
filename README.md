[![add-on registry](https://img.shields.io/badge/DDEV-Add--on_Registry-blue)](https://addons.ddev.com)
[![tests](https://github.com/stasadev/ddev-nvm/actions/workflows/tests.yml/badge.svg?branch=main)](https://github.com/stasadev/ddev-nvm/actions/workflows/tests.yml?query=branch%3Amain)
[![last commit](https://img.shields.io/github/last-commit/stasadev/ddev-nvm)](https://github.com/stasadev/ddev-nvm/commits)
[![release](https://img.shields.io/github/v/release/stasadev/ddev-nvm)](https://github.com/stasadev/ddev-nvm/releases/latest)

# DDEV Nvm

## Overview

This add-on integrates Nvm into your [DDEV](https://ddev.com/) project.

## Installation

```bash
ddev add-on get stasadev/ddev-nvm
ddev restart
```

After installation, make sure to commit the `.ddev` directory to version control.

## Usage

| Command | Description |
| ------- | ----------- |
| `ddev describe` | View service status and used ports for Nvm |
| `ddev logs -s nvm` | Check Nvm logs |

## Advanced Customization

To change the Docker image:

```bash
ddev dotenv set .ddev/.env.nvm --nvm-docker-image="ddev/ddev-utilities:latest"
ddev add-on get stasadev/ddev-nvm
ddev restart
```

Make sure to commit the `.ddev/.env.nvm` file to version control.

All customization options (use with caution):

| Variable | Flag | Default |
| -------- | ---- | ------- |
| `NVM_DOCKER_IMAGE` | `--nvm-docker-image` | `ddev/ddev-utilities:latest` |

## Credits

**Contributed and maintained by [@stasadev](https://github.com/stasadev)**
