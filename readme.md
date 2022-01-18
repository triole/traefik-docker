# Traefik-Docker

<!--- mdtoc: toc begin -->

1. [Synopsis](#synopsis)
2. [Prerequisites](#prerequisites)
3. [How to run?](#how-to-run-)<!--- mdtoc: toc end -->

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
