This repository is just some of my experiments in wrapping PHP applications in a docker image. The `/app` directory contains a simple PHP application, complete with composer support.

The entrypoint or root directory for the web application is `/app/public` and is the directory expected to be the web root for Apache or Nginx configurations. The experiments in this directory are simply to examine the different ways to launch the application and become more familiar with configuration and optimization of the environments.

**NOTE:** running these experiments assumes you have [docker](https://www.docker.com) installed and running on your machine.

## PHP on Nginx

The first experiment is launching PHP 7.2 in an Nginx environment to run this application. Notice that the docker build will install composer and set up the application completely.

#### Build the image
```sh
docker build . \
  -t <image-name> \
  -f Dockerfile
```

#### Run the image
```sh
docker run -it \
  -p 8080:80 \
  <image-name>
```
Navigate your browser to `http://localhost:8080/info.php` to see the configuration page.

## PHP on HHVM

The second experiment is launching PHP 7.2 in an HHVM environment to enable JIT compiling and optimization of the exact same application.

#### Build the image
```sh
docker build . \
  -t <image-name> \
  -f Dockerfile-hhvm
```

#### Run the image
```sh
docker run -it \
  -p 9080:80 \
  <image-name>
```
Navigate your browser to `http://localhost:9080/info.php` to see the configuration page.
