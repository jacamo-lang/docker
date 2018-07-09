# Dockerfile to run JaCaMo applications
# based on JaCaMo SNAPSHOT release

# to build:
#    docker build  -t jomifred/jacamo-runss .
#
# to run console applications:
#    cd <your application directory>
#    docker run -ti --rm --mount type=bind,source="$(pwd)",target=/app jomifred/jacamo-runss /app/<your .jcm file>
#
# to run GUI applications (on unix)
#    xhosts +
#    cd <your application directory>
#    docker run  -ti --rm -v /tmp/.X11-unix:/tmp/.X11-unix -e DISPLAY=$DISPLAY --mount type=bind,source="$(pwd)",target=/app jomifred/jacamo-runss /app/<your .jcm file>

FROM alpine

ENV JAVA_HOME /usr/lib/jvm/java-1.8-openjdk
ENV JACAMO_HOME=/jacamo/build
ENV PATH $PATH:$JAVA_HOME/bin:$JACAMO_HOME/scripts

RUN apk add --update --no-cache git gradle openjdk8-jre bash fontconfig
RUN apk add  ttf-dejavu 
RUN git clone https://github.com/jacamo-lang/jacamo.git && \
    cd jacamo && \
    gradle config

EXPOSE 3271
EXPOSE 3272
EXPOSE 3273

ENTRYPOINT [ "/jacamo/scripts/jacamo" ]
CMD []
