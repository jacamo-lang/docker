# docker for JaCaMo

This project contains docker instructions related to [JaCaMo](http://jacamo.sf.net) platform

## Buildind a JaCaMo release 

```shell
docker run --mount type=bind,source="$(pwd)",target=/jacamo/build/distributions jomifred/jacamo-release
```
  
