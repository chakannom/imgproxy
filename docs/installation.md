# Installation

There are three ways you can install imgproxy:

### Docker

imgproxy can (and should) be used as a standalone application inside a Docker container. Just pull the official image from Docker Hub:

```bash
$ docker pull darthsim/imgproxy:latest
$ docker run -p 8080:8080 -it darthsim/imgproxy
```

You can also build your own image. imgproxy is ready to be dockerized, plug and play:

```bash
$ docker build -t imgproxy .
$ docker run -p 8080:8080 -it imgproxy
```

### Heroku

imgproxy can be deployed to Heroku with a click of a button:

[![Deploy](https://www.herokucdn.com/deploy/button.svg)](https://heroku.com/deploy?template=https://github.com/DarthSim/imgproxy)

However, you can do it manually with a few steps:

```bash
$ git clone https://github.com/DarthSim/imgproxy.git && cd imgproxy
$ heroku create your-application
$ heroku stack:set container
$ git push heroku master
```

### From the source

1. First, install [libvips](https://github.com/libvips/libvips).

  ```bash
  # macOS
  $ brew tap homebrew/science
  $ brew install vips

  # Ubuntu
  # Ubuntu apt repository contains a pretty old version of libvips.
  # It's recommended to use PPA with an up to date version.
  $ sudo add-apt-repository ppa:dhor/myway
  $ sudo apt-get install libvips-dev
  
  # FreeBSD
  pkg install -y pkgconf vips

  # Windows
  # Download libvips(v8.6.4) : https://jcupitt.github.io/libvips/
  # Download pkg-config(v0.26) : https://sourceforge.net/projects/mingw-w64/files/Toolchains%20targetting%20Win64/Personal%20Builds/ray_linn/64bit-libraries/pkg-config/
  # Download golang(v.1.6.2) : https://golang.org/doc/install
  # Download mingw-w64(x86_64, win32) : http://mingw-w64.org/doku.php/download
  # **Windows Environment Variables**
  # PKG_CONFIG_PATH=~\vips-dev-8.6\lib\pkgconfig;~\vips-dev-8.6\share\pkgconfig;
  # GOPATH=~\Users\User\go
  # GOROOT=~\go
  # PAHT=~\vips-dev-8.6\bin;~\pkg-config\bin;~\go\bin;~\mingw64\bin
  ```

  **Note:** Most libvips packages come with WebP support. If you want libvips to support WebP on macOS, you need to install it this way:

  ```bash
  $ brew tap homebrew/science
  $ brew install vips --with-webp
  ```

2. Next, install imgproxy itself:

  ```bash
  $ go get -f -u github.com/DarthSim/imgproxy
  ```
