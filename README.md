<p align="center"><a href="#readme"><img src=".github/images/card.svg"/></a></p>

<p align="center">
  <a href="https://kaos.sh/w/golang/cd"><img src="https://kaos.sh/w/golang/cd.svg" alt="GitHub Actions CD Status" /></a>
  <a href="#license"><img src=".github/images/license.svg"/></a>
</p>

This repository contains Dockerfiles with Golang images based on [Alpine](https://www.alpinelinux.org), [AlmaLinux](https://almalinux.org) and [OracleLinux](https://www.oracle.com/linux/).

### Usage

Images in [GitHub Container Registry](https://kaos.sh/p/golang):

- `ghcr.io/essentialkaos/golang:alpine3.19`
- `ghcr.io/essentialkaos/golang:alpine3.20`
- `ghcr.io/essentialkaos/golang:alpine3.21`
- `ghcr.io/essentialkaos/golang:alpine3.22`
- `ghcr.io/essentialkaos/golang:ol8`
- `ghcr.io/essentialkaos/golang:ol9`
- `ghcr.io/essentialkaos/golang:ol10`
- `ghcr.io/essentialkaos/golang:alma8`
- `ghcr.io/essentialkaos/golang:alma9`
- `ghcr.io/essentialkaos/golang:alma10`

Images in [DockerHub](https://kaos.sh/d/golang):

- `essentialkaos/golang:alpine3.19`
- `essentialkaos/golang:alpine3.20`
- `essentialkaos/golang:alpine3.21`
- `essentialkaos/golang:alpine3.22`
- `essentialkaos/golang:ol8`
- `essentialkaos/golang:ol9`
- `essentialkaos/golang:ol10`
- `essentialkaos/golang:alma8`
- `essentialkaos/golang:alma9`
- `essentialkaos/golang:alma10`

### Usage example

```dockerfile
## REGISTRY CONFIGURATION ######################################################

ARG REGISTRY="docker.io"

## BUILDER #####################################################################

FROM ${REGISTRY}/essentialkaos/golang:alpine3.22 AS builder

WORKDIR /go/src/github.com/johndoe/app

COPY . .

RUN make deps && make all

## FINAL IMAGE #################################################################

FROM ${REGISTRY}/essentialkaos/alpine:3.22 AS final

COPY --from=builder /go/src/github.com/johndoe/app/app /usr/bin/

# hadolint ignore=DL3018
RUN apk add --no-cache ca-certificates

ENTRYPOINT ["app"]

################################################################################
```

### Contributing

Before contributing to this project please read our [Contributing Guidelines](https://github.com/essentialkaos/contributing-guidelines#contributing-guidelines).

### License

[Apache License, Version 2.0](http://www.apache.org/licenses/LICENSE-2.0)

<p align="center"><a href="https://essentialkaos.com"><img src="https://raw.githubusercontent.com/essentialkaos/.github/refs/heads/master/images/ekgh.svg"/></a></p>
