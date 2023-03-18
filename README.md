# Neko Apps

[Neko](https://github.com/m1k1o/neko) is open source virtual browser run in a docker container, that can be accessed from a webpage. It does not have to be only web browser. It can be anything.

Best served with [neko-rooms](https://github.com/m1k1o/neko-rooms), simple room management for neko.

## How to build

You can build any container by calling `./build` binary. Use dir name as application name to build.

```sh
./build <dir-name>
```

You can copy `.env` to `.env.local` and modify your build image or neko base image.

Your new image will be tagged as `m1k1o/neko-apps:<dir-name>`

### For nvidia- images

You need to go to neko repo and build `nvidia-base` image first.

## How to run

Please follow [getting started](https://neko.m1k1o.net/#/getting-started/examples) guide from neko or neko-rooms.
