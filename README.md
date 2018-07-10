# docker for JaCaMo

This project contains docker instructions related to [JaCaMo](http://jacamo.sf.net) platform

## Running JaCaMo applications

Commands for console applications:

 ```
cd <your application directory>
docker run -ti --rm \
       -v "$(pwd)":/app \
       jomifred/jacamo-runss /app/<your .jcm file>
```

Commands for GUI applications (on unix):

```
xhosts +
cd <your application directory>
docker run  -ti --rm \
       -v /tmp/.X11-unix:/tmp/.X11-unix -e DISPLAY=$DISPLAY \
       -v "$(pwd)":/app \
       jomifred/jacamo-runss /app/<your .jcm file>
```


## Buildind a JaCaMo release

```
docker run -v "$(pwd)":/jacamo/build/distributions jomifred/jacamo-release
```
