# Hugo

[![Docker Pulls](https://img.shields.io/docker/pulls/klakegg/hugo.svg)](https://store.docker.com/community/images/klakegg/hugo)

Truly minimal Docker images for [Hugo](http://gohugo.io/) with batteries included.
These images sets `bind` when started as server, otherwise no magic.

## Latest tags

Minimal image based upon [Alpine](https://hub.docker.com/r/_/alpine/):

* Aliases: `alpine`, `ext-alpine`
* Hugo NEXT: `NEXT-alpine`, `NEXT-ext-alpine`

Minimal image based upon [Alpine](https://hub.docker.com/r/_/alpine/) with [Asciidoctor](http://asciidoctor.org/) installed:

* Aliases: `asciidoctor`, `ext-asciidoctor`
* Hugo NEXT: `NEXT-asciidoctor`, `NEXT-ext-asciidoctor`, `NEXT-ext-asciidoctor-ci`, `NEXT-ext-asciidoctor-onbuild`

Minimal image based upon [Alpine](https://hub.docker.com/r/_/alpine/) with [Pandoc](https://pandoc.org/) installed:

* Aliases: `pandoc`, `ext-pandoc`
* Hugo NEXT: `NEXT-pandoc`, `NEXT-ext-pandoc`

Image based upon [Debian](https://hub.docker.com/r/_/debian/):

* Aliases: `debian`, `ext`, `latest-ext`, `ext-debian`
* Hugo NEXT: `NEXT-debian`, `NEXT-ext`, `NEXT-ext-debian`

Image based upon [Ubuntu](https://hub.docker.com/r/_/ubuntu/):

* Aliases: `ubuntu`, `ext-ubuntu`
* Hugo NEXT: `NEXT-ubuntu`, `NEXT-ext-ubuntu`

*Looking for older tags? Please see the [complete list of tags](https://github.com/klakegg/docker-hugo/blob/master/doc/tags.md).*

## Using image

This image does not try to do any fancy.
Users may use Hugo [just as they are used to](https://gohugo.io/documentation/).

## Hugo shell

A Hugo shell is made available in the Alpine/Debian/Ubuntu images (including Asciidoctor/Pandoc images).
Hugo shell is bash and Hugo completion.

To get into a shell for your site:

```shell
docker run --rm -it \
  -v $(pwd):/src \
  klakegg/hugo:NEXT-alpine \
  shell
```

## Hugo extended edition

The extended edition is used in those images containing `ext` in the name. Except use of extended edition and additional tools are those images exactly the same as those using the normal edition.

Table of Hugo extention features and the version when images first support the feature:

| Feature       | Alpine | Debian | Ubuntu |
| ------------- | ------ | ------ | ------ |
| Hugo extended | 0.43   | 0.43   | 0.43   |
| PostCSS       | 0.56.0 | 0.43   | 0.43   |
| NodeJS        | 0.54.0 | 0.54.0 | 0.54.0 |
| Yarn          | 0.54.0 | 0.54.0 | 0.54.0 |
| Git           | 0.56.0 | 0.56.0 | 0.56.0 |
| Autoprefixer  | 0.57.0 | 0.57.0 | 0.57.0 |
| Go            | 0.68.0 | 0.68.0 | 0.68.0 |
| Babel         | 0.71.0 | 0.71.0 | 0.71.0 |
| rst2html      | 0.81.0 | 0.81.0 | 0.81.0 |

Users of [google/docsy](https://github.com/google/docsy) may use the extended images as of version 0.57.2 to build their site.

## Using Pandoc

Hugo images with Pandoc support are made available for users wanting to use Pandoc in combination with Hugo.

[Hugo triggers Pandoc](https://gohugo.io/content-management/formats/#additional-formats-through-external-helpers) with `pandoc --mathjax`.
Some users may want to use other arguments, so to accommodate such a need is an alias `pandoc` created with the content of `HUGO_PANDOC` (default: `pandoc-default`) upon initiation.
The `pandoc` executable is renamed to `pandoc-default` as a new `pandoc` script is provided to hanle the `HUGO_PANDOC` evironment variable.

Example of explicit setting `pandoc` alias:

```shell
docker run --rm -it \
  -v $(pwd):/src \
  -e HUGO_PANDOC="pandoc-default --strip-empty-paragraphs" \
  klakegg/hugo:NEXT-pandoc
```

## Overriding entrypoint

Those wanting to override entrypoint in the image may easily do so.

Default entrypoint is `hugo`, a small script wrapping the official Hugo software. If you want to use the official software without any wrapping may you use `hugo-official` as entrypoint.

On command line using `--entrypoint`:

```shell
docker run --rm -it \
  -v $(pwd):/src \
  --entrypoint hugo-official \
  klakegg/hugo:NEXT
```

In docker-compose using `entrypoint`:

```yaml
  build:
    image: klakegg/hugo:NEXT
    entrypoint: hugo-official
    volumes:
      - ".:/src"
```


## Versions

| Software | Version |
| -------- | ------- |
| Go       | 1.16.2  |
| NodeJS   | 18.x    |
| Pandoc   | 2.12    |
| Yarn     | 1.22.10 |


## Configuration

Environment variables:
* HUGO_BIND - Bind address for server. Default: `0.0.0.0`
* HUGO_CACHEDIR - Cache directory for modules. Default: `/tmp`
* HUGO_DESTINATION - Location of output folder. Default: `public`
* HUGO_PANDOC - Pandoc command to be triggered. Default: `pandoc-default`
* HUGO_ENV - Selecting environment ("DEV"/"production"). Default: `DEV`
* HUGO_VERSION - Version of Hugo bundled in image. Default: *Current version*
* HUGO_VERSION_OVERRIDE - Version of Hugo to use. Requires images for Hugo 0.71.1 or newer. Default: *blank*

Ports:
* `1313/tcp`
