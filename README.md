# gpt4all-docker

Sophisticated docker builds for parent project [nomic-ai/gpt4all](https://github.com/nomic-ai/gpt4all) - the new monorepo. 

![example workflow](https://github.com/localagi/gpt4all-docker/actions/workflows/publish-docker.yml/badge.svg?branch=main)

Easy setup. Compatible. Tweakable. Scaleable.

#### Naming scheme

The builds are based on [gpt4all monorepo](https://github.com/nomic-ai/gpt4all).
`-cli` means the container is able to provide the cli.


#### Supported platforms
`amd64`, `arm64`

#### Supported versions
only `main` supported

See [Releases](../../releases)

## Prerequisites

* `docker` and `docker compose` are available on your system

## Run

### cli

`docker run localagi/gpt4all-cli:main --help`


### Get the latest builds / update
`docker compose pull`

### Cleanup
`docker compose rm`

## Contributing

When there is a new version and there is need of builds or you require the latest main build, feel free to open an issue

## Problems?

Open an issue on the [Issue Tracker](../../issues)

## Limitations
We cannot support issues regarding the base software. Please refer to the main project page mentioned in the second line of this card.

