# Dockerfile to run JaCaMo applications
# based on JaCaMo SNAPSHOT release (0.10)

# to build:
#    docker build  -t jomifred/jacamo-runss .

FROM alpine

ENV JAVA_HOME /usr/lib/jvm/java-1.8-openjdk
ENV JACAMO_HOME=/jacamo/build
ENV PATH $PATH:$JAVA_HOME/bin:$JACAMO_HOME/scripts

RUN apk add --update --no-cache git gradle openjdk8-jre bash fontconfig ttf-dejavu graphviz
RUN git clone https://github.com/jacamo-lang/jacamo.git && \
    cd jacamo && \
    gradle config

EXPOSE 3271
EXPOSE 3272
EXPOSE 3273

#ENTRYPOINT [ "/jacamo/build/scripts/jacamo" ]
#CMD []
