FROM alpine:3.3

ENV BLAS=/usr/local/lib/libfblas.a \
    LAPACK=/usr/local/lib/liblapack.a
RUN apk add --update --no-cache musl python3-dev freetype-dev make g++ gfortran && \
    apk add --no-cache --virtual=build-dependencies wget && \
    cd /tmp && wget -q --no-check-certificate \
        https://raw.githubusercontent.com/catholabs/docker-alpine/master/blas.sh \
        https://raw.githubusercontent.com/catholabs/docker-alpine/master/blas.tgz \
        https://raw.githubusercontent.com/catholabs/docker-alpine/master/lapack.sh \
        https://raw.githubusercontent.com/catholabs/docker-alpine/master/lapack.tgz \
        https://raw.githubusercontent.com/catholabs/docker-alpine/master/make.inc && \
    sh ./blas.sh && sh ./lapack.sh && \
    cp ~/src/BLAS/libfblas.a /usr/local/lib && \
    cp ~/src/lapack-3.5.0/liblapack.a /usr/local/lib && \
    wget -q --no-check-certificate "https://bootstrap.pypa.io/get-pip.py" -O /dev/stdout | python3 && \
    pip install numpy==1.9.3 && \
    pip install networkx pandas pyyaml more_itertools && \
    apk del build-dependencies && \
    rm -rf /var/cache/apk/* /tmp/* /root/src/
CMD ["sh"]
