# heroku-buildpack-pdftk-java

Adds a `pdftk` wrapper script so the pdftk-java apt package will run on heroku

## Context

The `heroku-community/apt` buildpack is mostly-successful at installing `apt` packages and `.deb` files, but it doesn't run post-install scripts and it installs everything in the `/app/.apt` directory.

This buildpack just creates a custom wrapper script that's aware that all the apt packages are installed in `/app/.apt` instead of the system root.

## Usage

This buildpack is not meant to be used on its own, and instead should be in used in combination with Heroku's [multiple buildpack support](https://devcenter.heroku.com/articles/using-multiple-buildpacks-for-an-app).

You will need the `heroku/jvm` buildpack, the  `heroku-community/apt` buildpack, and an `Aptfile` that installs pdftk and its relevant dependencies

Example `Aptfile`:

```
libbcprov-java
libcommons-lang3-java
http://mirrors.kernel.org/ubuntu/pool/universe/p/pdftk-java/pdftk-java_3.0.6-1_all.deb
```

## License

MIT
