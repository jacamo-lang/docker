# Dockerfile to create an image that produces a release of JaCaMo
# (a zip file with all necessary to install JaCaMo)

# to build: docker build  -t jomifred/jacamo-release .

FROM alpine

RUN apk add --update git gradle

# from https://github.com/rochdev/docker-alpine-asciidoctor/blob/master/full/Dockerfile

ENV JAVA_HOME /usr/lib/jvm/java-1.8-openjdk
ENV PATH $PATH:$JAVA_HOME/bin
ENV LIBRARY_PATH=/lib:/usr/lib
ENV BACKENDS /asciidoctor-backends
ENV GVM_AUTO_ANSWER true
ENV PYGMENTS_PATH=/pygments-jacamo/pygments

RUN apk add --update --no-cache gcc g++ make bash curl unzip tar openjdk8-jre ruby-dev ruby ruby-nokogiri ruby-json asciidoctor python python-dev py-setuptools py-pip ttf-dejavu graphviz libjpeg-turbo libjpeg-turbo-dev zlib zlib-dev zip mercurial && \
    gem install --no-ri --no-rdoc asciidoctor-diagram && \
    gem install --no-ri --no-rdoc asciidoctor-pdf --pre && \
    gem install --no-ri --no-rdoc asciidoctor-epub3 --pre && \
    gem install --no-ri --no-rdoc asciidoctor-confluence && \
    gem install --no-ri --no-rdoc asciidoctor-rouge && \
    gem install --no-ri --no-rdoc coderay pygments.rb thread_safe epubcheck kindlegen && \
    gem install --no-ri --no-rdoc slim && \
    gem install --no-ri --no-rdoc haml tilt && \
    gem cleanup && \
    mkdir $BACKENDS && \
    curl -LkSs https://api.github.com/repos/asciidoctor/asciidoctor-backends/tarball | tar xfz - -C $BACKENDS --strip-components=1 && \
    pip install "blockdiag[pdf]" && \
    pip install  seqdiag && \
    pip install  actdiag && \
    pip install  nwdiag && \
    (curl -s get.sdkman.io | bash) && \
    /bin/bash -c "echo sdkman_auto_answer=true > ~/.sdkman/etc/config" && \
    /bin/bash -c -l "source ~/.sdkman/bin/sdkman-init.sh && sdk install lazybones" && \
    /bin/bash -c -l "source ~/.sdkman/bin/sdkman-init.sh && sdk flush archives" && \
    /bin/bash -c -l "source ~/.sdkman/bin/sdkman-init.sh && sdk flush temp" && \
#
    hg clone https://jomi_hubner@bitbucket.org/jomi_hubner/pygments-jacamo && \
    cd pygments-jacamo && make mapfiles && \
    python setup.py install && \
#
    apk del bash curl unzip tar gcc g++ make ruby-dev python-dev py-pip libjpeg-turbo-dev zlib-dev zip mercurial && \
    rm -rf /tmp/* /var/cache/apk/* ~/.cache/pip

RUN git clone https://github.com/jacamo-lang/jacamo.git && \
    cd jacamo && \
    gradle test

ENTRYPOINT cd jacamo && git pull && gradle release
