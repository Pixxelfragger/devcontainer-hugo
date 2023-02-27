# VS Code devcontainer for Hugo

![pipeline status](https://github.com/pixxelfragger/devcontainer-hugo/actions/workflows/docker.yml/badge.svg?branch=master)

[![Docker Pulls](https://img.shields.io/docker/pulls/pixxelfragger/devcontainer-hugo.svg)](https://store.docker.com/community/images/pixxelfragger/devcontainer-hugo)
[![Docker Image Version (latest semver)](https://img.shields.io/docker/v/pixxelfragger/devcontainer-hugo?sort=semver)](https://hub.docker.com/r/pixxelfragger/devcontainer-hugo)

> WORK IN PROGRESS!
> 
> TODO:
> 
> - [ ] add zsh autocompletion
> - [ ] add pandoc and asciidoctor ubuntu and debian images
> - [ ] add examples for usage with devcontainer.json
> - [ ] add examples for usage wit "Docker Desktop - Dev Environment"

---

This is a [VS Code devcontainer](https://code.visualstudio.com/docs/remote/containers) for [Hugo](https://gohugo.io/).

The image is available for the following architectures:

- `amd64`
- `arm64`

> `arm/v7` is not available as there is no devcontainer base image for it available.

The image is based on the [klakegg/hugo](https://hub.docker.com/r/klakegg/hugo) image. Which is described as:

>Truly minimal Docker images for [Hugo](http://gohugo.io/) with batteries included.
>These images sets `bind` when started as server, otherwise no magic.

## What is changed?

So as the `klakegg/hugo` images are a great build for builds or CI/CD, but they are not really suited for development usage as devcontainers.
So this image is based on the `klakegg/hugo` image, but with some changes:

- there is no busybox image
- there is only the main and extended versions are available (no `ci` or `onbuild` tags)
- the image is based on the alpine, debian and ubuntu devcontainer base images.

*Looking for older tags? Please see the [complete list of tags](https://github.com/pixxelfragger/devcontainer-hugo/blob/master/doc/tags.md).*

## Using image

> TODO: add some examples of how to use the image
> partly done, but needs more examples: [devcontainer usage](https://github.com/pixxelfragger/devcontainer-hugo/blob/master/doc/example/decvontainer-usage.md).

## Hugo extended edition

The extended edition is used in those images containing `ext` in the name. Except use of extended edition and additional tools are those images exactly the same as those using the normal edition.

Users of [google/docsy](https://github.com/google/docsy) may use the extended images as of version 0.57.2 to build their site.

## Configuration

Environment variables:

- HUGO_BIND - Bind address for server. Default: `0.0.0.0`
- HUGO_CACHEDIR - Cache directory for modules. Default: `/tmp`
- HUGO_DESTINATION - Location of output folder. Default: `public`
- HUGO_PANDOC - Pandoc command to be triggered. Default: `pandoc-default`
- HUGO_ENV - Selecting environment ("DEV"/"production"). Default: `DEV`
- HUGO_VERSION - Version of Hugo bundled in image. Default: *Current version*
- HUGO_VERSION_OVERRIDE - Version of Hugo to use. Default: *blank*

Ports:
- `1313/tcp`
