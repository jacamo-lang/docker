# Docker for JaCaMo

This project contains docker instructions related to [JaCaMo](http://jacamo.sf.net) platform.

[Docker Hub link](https://hub.docker.com/r/jomifred/jacamo)

## Creating JaCaMo applications

To create an application identified by `helloworld`, enter the following command:
```
docker run -ti --rm -v .:/app -v ./gcache:/root/.gradle jomifred/jacamo:1.2 app create /app/helloworld --console
```

NB: the tag `1.2` correspond to the version of JaCaMo.

## Running JaCaMo applications

Commands for console applications (assuming it was created as above):

```
cd helloworld
docker run -ti --rm -v .:/app -v ./gcache:/root/.gradle -w /app jomifred/jacamo:1.2 helloworld.jcm
```

Commands for GUI applications (on unix):

```
xhost +
cd <your application directory>
docker run  -ti --rm -e DISPLAY=host.docker.internal:0 -v .:/app -w /app jomifred/jacamo:1.2 <your .jcm file>
```
