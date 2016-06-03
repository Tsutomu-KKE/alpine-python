#FROM frolvlad/alpine-glibc
FROM tsutomu7/alpine-glibc

ENV PATH=/opt/conda/bin:$PATH \
    LANG=C \
    MINICONDA=Miniconda3-latest-Linux-x86_64.sh
RUN apk add --no-cache --virtual=build-dependencies bash wget tzdata && \
    cp /usr/share/zoneinfo/Japan /etc/localtime && \
    wget -q --no-check-certificate https://repo.continuum.io/miniconda/$MINICONDA && \
    bash /$MINICONDA -b -p /opt/conda && \
    conda update -y conda && \
    pip install -U pip && \
    ln -s /opt/conda/bin/* /usr/local/bin/ && \
    apk del build-dependencies && \
    find /opt -name __pycache__ | xargs rm -r && \
    rm -rf /root/.[acpw]* /$MINICONDA /opt/conda/pkgs/*
CMD ["sh"]

