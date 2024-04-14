
<p align="center"><a href="#readme"><img src="https://gh.kaos.st/golang.svg"/></a></p>

<p align="center">
  <a href="https://kaos.sh/w/golang/cd"><img src="https://kaos.sh/w/golang/cd.svg" alt="GitHub Actions CD Status" /></a>
  <a href="#license"><img src="https://gh.kaos.st/apache2.svg"></a>
</p>

This repository contains Dockerfiles with Golang images based on Alpine and OracleLinux.

### Usage

Images in [GitHub Container Registry](https://kaos.sh/p/golang):

- `ghcr.io/essentialkaos/golang:alpine3.15`
- `ghcr.io/essentialkaos/golang:alpine3.16`
- `ghcr.io/essentialkaos/golang:alpine3.17`
- `ghcr.io/essentialkaos/golang:alpine3.18`
- `ghcr.io/essentialkaos/golang:alpine3.19`
- `ghcr.io/essentialkaos/golang:ol8`
- `ghcr.io/essentialkaos/golang:ol9`

Images in [DockerHub](https://kaos.sh/d/golang):

- `essentialkaos/golang:alpine3.15`
- `essentialkaos/golang:alpine3.16`
- `essentialkaos/golang:alpine3.17`
- `essentialkaos/golang:alpine3.18`
- `essentialkaos/golang:alpine3.19`
- `essentialkaos/golang:ol8`
- `essentialkaos/golang:ol9`

### Usage example

```dockerfile
## REGISTRY CONFIGURATION ######################################################

ARG REGISTRY="docker.io"

## BUILDER #####################################################################

FROM ${REGISTRY}/essentialkaos/golang:alpine3.17 as builder

WORKDIR /go/src/github.com/johndoe/app

COPY . .

RUN make deps && make all

## FINAL IMAGE #################################################################

FROM ${REGISTRY}/essentialkaos/alpine:3.17

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

<p align="center"><a href="https://essentialkaos.com"><img src="https://gh.kaos.st/ekgh.svg"/></a></p>
