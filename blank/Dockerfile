FROM frolvlad/alpine-glibc

ENV PATH=/opt/conda/bin:$PATH \
    LANG=C.UTF-8 \
    MINICONDA=Miniconda3-latest-Linux-x86_64.sh
RUN apk add --no-cache --virtual=build-dependencies bash wget tzdata && \
    cp /usr/share/zoneinfo/Japan /etc/localtime && \
    wget -q --no-check-certificate https://repo.continuum.io/miniconda/$MINICONDA && \
    bash /$MINICONDA -b -p /opt/conda && \
    conda update -y conda pip setuptools anaconda-client && \
    ln -s /opt/conda/bin/* /usr/local/bin/ && \
    apk del build-dependencies && \
    find /opt -name __pycache__ | xargs rm -r && \
    rm -rf /root/.[apw]* /$MINICONDA /opt/conda/pkgs/*
CMD ["sh"]

