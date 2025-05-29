# Neko Apps

[Neko](https://github.com/m1k1o/neko) is open source virtual browser run in a docker container, that can be accessed from a webpage. It does not have to be only web browser. It can be anything.

Best served with [neko-rooms](https://github.com/m1k1o/neko-rooms), simple room management for neko.

## How to build

You can build any container by calling `./build` binary. Use dir name as application name to build.

```sh
./build --application <application_name>
./build --application <application_name> --base_image ghcr.io/m1k1o/neko/base:latest
```

Your new image will be tagged as `ghcr.io/m1k1o/neko-apps/<application_name>`

### For flavored images (e.g. `nvidia`)

```sh
./build --flavor <flavor> --application <application_name>
```

Your new image will be tagged as `ghcr.io/m1k1o/neko-apps/<flavor>-<application_name>`

## How to run

Please follow [getting started](https://neko.m1k1o.net/docs/v3/quick-start) guide in neko documentation.
