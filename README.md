Go
==

Simple docker image for running the [Go](https://golang.org) compiler in a container.  Most distributions ship old versions of the golang packages.  Containerizing Go allows much newer versions to be used without hacking around with ppa's.

Usage
-----

The image mounts the directory located at `GOPATH` inside the container at /go, and assigns this directory to the `GOPATH` environment variable in the container.  It expects at least 2 arguments:

- the current directory relative to the host GOPATH, and
- the Go command to run.

For example, given a `GOPATH` of `~/code/godev`, with a project located at `~/code/godev/src/github.com/t3hpr1m3/hello`, the following command would compile the application:

```shell
$ docker run \
    --rm -t \
    -v $GOPATH:/go \
    --name golang \
    t3hpr1m3/golang:1.5.1 \
    src/github.com/t3hpr1m3/hello \
    build
```

An example bash function that wraps the entire command, allowing the user to simply execute `go build` and run the entire build process in a container automatically, can be found [here](https://github.com/t3hpr1m3/dotfiles/blob/master/home/.docker_wrappers#L26).
