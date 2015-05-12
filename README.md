# Docker Exec Image: F#

A Dockerfile describing an container capable of executing F# source files.

# Build

```sh
git clone https://github.com/docker-exec/fsharp.git
docker build -t dexec/lang-fsharp .
```

# Usage

In a directory containing a script e.g. foo.fs, run:

```sh
docker run -t --rm \
    -v $(pwd -P)/foo.fs:/tmp/dexec/build/foo.fs \
    dexec/lang-fsharp foo.fs
```

## Passing arguments to the script

Arguments can be passed to the script using any of the following forms:

```
-a argument
--arg argument
--arg=argument
```

Each argument passed must be prefixed in this way, e.g.

```sh
docker run -t --rm \
    -v $(pwd -P)/foo.fs:/tmp/dexec/build/foo.fs \
    dexec/lang-fsharp foo.fs \
    --arg='hello world' \
    --arg=foo \
    --arg=bar
```

## Passing arguments to the compiler

Arguments can be passed to the compiler using any of the following forms:

```
-b argument
--build-arg argument
--build-arg=argument
```

Each argument passed must be prefixed in this way, e.g.

```sh
docker run -t --rm \
    -v $(pwd -P)/foo.fs:/tmp/dexec/build/foo.fs \
    dexec/lang-fsharp foo.fs \
    --build-arg=-some-compiler-option \
    --build-arg=some-compiler-option-value
```
