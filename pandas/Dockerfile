#FROM frolvlad/alpine-glibc
FROM tsutomu7/alpine-glibc

ENV PATH=/opt/conda/bin:$PATH \
    LANG=C \
    MINICONDA=Miniconda3-latest-Linux-x86_64.sh
RUN apk add --no-cache libstdc++ && \
    apk add --no-cache --virtual=build-dependencies bash wget tzdata && \
    cp /usr/share/zoneinfo/Japan /etc/localtime && \
    wget -q --no-check-certificate https://repo.continuum.io/miniconda/$MINICONDA && \
    bash /$MINICONDA -b -p /opt/conda && \
    conda update -y conda && \
    conda install -y nomkl numpy networkx pandas pyyaml && \
    pip install -U pip && \
    pip install more_itertools && \
    ln -s /opt/conda/bin/* /usr/local/bin/ && \
    apk del build-dependencies && \
    find /opt -name __pycache__ | xargs rm -r && \
    cd / && rm -rf /root/.[acpw]* /$MINICONDA /ipaexg00301* /opt/conda/pkgs/* \
        /opt/conda/lib/python3.5/site-packages/pulp/solverdir/cbc/[ow]* \
        /opt/conda/lib/python3.5/site-packages/pulp/solverdir/cbc/linux/32
CMD ["sh"]
