FROM frolvlad/alpine-glibc

ENV PATH=/opt/conda/bin:$PATH \
    LANG=C.UTF-8 \
    MINICONDA=Miniconda3-latest-Linux-x86_64.sh
RUN apk add --no-cache bash wget && \
    wget -q --no-check-certificate https://repo.continuum.io/miniconda/$MINICONDA && \
    bash /$MINICONDA -b -p /opt/conda && \
    ln -s /opt/conda/bin/* /usr/local/bin/ && \
    find /opt -name __pycache__ | xargs rm -r && \
    rm -rf /root/.[acpw]* /$MINICONDA /opt/conda/pkgs/*
CMD ["bash"]

