FROM frolvlad/alpine-glibc

ENV PATH=/opt/conda/bin:$PATH \
    LANG=C.UTF-8 \
    MINICONDA=Miniconda3-latest-Linux-x86_64.sh
RUN apk add --no-cache --virtual=build-dependencies bash wget && \
    wget -q --no-check-certificate https://repo.continuum.io/miniconda/$MINICONDA && \
    bash /Miniconda3-latest-Linux-x86_64.sh -b -p /opt/conda && \
    conda install -y nomkl numpy networkx pandas pyyaml && \
    pip install more_itertools && \
    ln -s /opt/conda/bin/* /usr/local/bin/ && \
    apk del build-dependencies && \
    rm -rf /root/.[acpw]* /$MINICONDA /opt/conda/pkgs/*
CMD ["sh"]

