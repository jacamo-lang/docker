# Docker for JaCaMo

This project contains docker instructions related to [JaCaMo](http://jacamo.sf.net) platform.

[Docker Hub link](https://hub.docker.com/r/jomifred/jacamo)

## Creating JaCaMo applications

To create an application identified by `helloworld`, enter the following command:
```
docker run -ti --rm -v "$(pwd)":/app jomifred/jacamo:1.0 jacamo-new-project /app/helloworld
```

NB: the tag `1.0` correspond to the version of JaCaMo.

## Running JaCaMo applications

Commands for console applications:

```
cd <your application directory>
docker run -ti --rm -v "$(pwd)":/app -w /app jomifred/jacamo:1.0 jacamo <your .jcm file>
```

Commands for GUI applications (on unix):

```
xhost +
cd <your application directory>
docker run  -ti --rm -e DISPLAY=host.docker.internal:0 -v "$(pwd)":/app -w /app jomifred/jacamo:1.0 jacamo <your .jcm file>
```
