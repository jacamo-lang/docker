# Docker for JaCaMo

This project contains docker instructions related to [JaCaMo](http://jacamo.sf.net) platform

## Creating JaCaMo applications

To create an application identified by `helloworld`, enter the following command:
```
docker run -ti --rm -v "$(pwd)":/app jomifred/jacamo-createss /app/helloworld
```

## Running JaCaMo applications

Commands for console applications:

```
cd <your application directory>
docker run -ti --rm -v "$(pwd)":/app -w /app jomifred/jacamo-runss jacamo <your .jcm file>
```

or

```
cd <your application directory>
docker run -ti -v "$(pwd)":/app -w /app jomifred/jacamo-runss gradle
```


Commands for GUI applications (on unix):

```
xhost +
cd <your application directory>
docker run  -ti --rm \
       -v /tmp/.X11-unix:/tmp/.X11-unix -e DISPLAY=$DISPLAY \
       -v "$(pwd)":/app \
       -w /app
       jomifred/jacamo-runss jacamo <your .jcm file>
```


## Building a JaCaMo release

from the latest version in GitHub

```
docker run -v "$(pwd)":/jacamo/build/distributions jomifred/jacamo-release
```
