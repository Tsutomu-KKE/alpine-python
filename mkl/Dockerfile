FROM frolvlad/alpine-glibc

ENV PATH=/opt/conda/bin:$PATH \
    LANG=C.UTF-8 \
    MINICONDA=Miniconda3-latest-Linux-x86_64.sh
RUN apk add --no-cache libstdc++ && \
    apk add --no-cache --virtual=build-dependencies bash wget tzdata && \
    cp /usr/share/zoneinfo/Japan /etc/localtime && \
    wget -q --no-check-certificate https://repo.continuum.io/miniconda/$MINICONDA \
        http://dl.ipafont.ipa.go.jp/IPAexfont/ipaexg00301.zip && \
    bash /$MINICONDA -b -p /opt/conda && \
    conda update -y conda pip setuptools && \
    conda install -y matplotlib networkx scikit-learn jupyter blist \
        bokeh statsmodels ncurses seaborn dask flask markdown sympy psutil && \
    pip install --no-cache more_itertools pulp pyjade && \
    unzip -q ipaexg00301.zip && \
    mkdir -p /usr/share/fonts/ && \
    mv /ipaexg00301/ipaexg.ttf /usr/share/fonts/ && \
    ln -s /opt/conda/bin/* /usr/local/bin/ && \
    apk del build-dependencies && \
    find /opt -name __pycache__ | xargs rm -r && \
    cd / && rm -rf /root/.[apw]* /$MINICONDA /ipaexg00301* /opt/conda/pkgs/* \
        /opt/conda/lib/python3.5/site-packages/pulp/solverdir/cbc/[ow]* \
        /opt/conda/lib/python3.5/site-packages/pulp/solverdir/cbc/linux/32
CMD ["sh"]
