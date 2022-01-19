# Traefik-Docker

<!--- mdtoc: toc begin -->

1. [Synopsis](#synopsis)
2. [Prerequisites](#prerequisites)
3. [How to run?](#how-to-run-)
4. [Known problems](#known-problems)
   1. [At least libseccomp 2.4.2 on your host](#at-least-libseccomp-2-4-2-on-your-host)<!--- mdtoc: toc end -->

## Synopsis

This is a simple [Traefik](https://doc.traefik.io/traefik/) docker setup. It is simple and based on Alpine to provide true cross architecture compatibility.

## Prerequisites

1. Having [Task](taskfile.dev/) because it is used to simplify build and run processes

2. Before the docker build this setup tries to fetch the Treafik binary from the system. Its path needs to be in `$PATH` so that the command `which traefik` delivers something processable.

## How to run?

As usual a `Taskfile` can be found.

```shell
# build and run
task

# list of all available tasks
task -l
```

## Known problems

### At least libseccomp 2.4.2 on your host

Running `apk update` inside the container produces errors if the `libseccomp` version on your host is older that 2.4.2. Running this docker setup on Raspbian and CentOS produced these kind of errors.

If you cannot upgrade the `libseccomp` library, a possible fix is to downgrade the docker base image to 3.12 where the problem does not exist. You could do `FROM alpine:3.12`.

Cause of the issue is the date inside the container being wrong which makes the TLS certificate validation impossible.
