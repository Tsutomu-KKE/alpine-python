FROM frolvlad/alpine-glibc

ENV PATH=/opt/conda/bin:$PATH \
    LANG=C.UTF-8 \
    MINICONDA=Miniconda3-latest-Linux-x86_64.sh
RUN apk add --no-cache libstdc++ && \
    apk add --no-cache --virtual=build-dependencies bash wget && \
    wget -q --no-check-certificate https://repo.continuum.io/miniconda/$MINICONDA \
        https://github.com/ipython-contrib/IPython-notebook-extensions/archive/master.zip \
        https://raw.githubusercontent.com/Tsutomu-KKE/scientific-python/master/notebook.json \
        http://dl.ipafont.ipa.go.jp/IPAexfont/ipaexg00301.zip && \
    bash /Miniconda3-latest-Linux-x86_64.sh -b -p /opt/conda && \
    conda install -y matplotlib networkx scikit-learn jupyter blist \
        bokeh statsmodels ncurses seaborn blaze dask flask markdown sympy && \
    pip install more_itertools pulp pyjade && \
    unzip -q ipaexg00301.zip && \
    mv /ipaexg00301/ipaexg.ttf /opt/conda/lib/python3.5/site-packages/matplotlib/mpl-data/fonts/ttf/ && \
    unzip -q master.zip && \
    mkdir -p /root/.local/share/jupyter/ && \
    mkdir -p /root/.jupyter/nbconfig/ && \
    mv notebook.json /root/.jupyter/nbconfig/ && \
    cd IPython-notebook-extensions-master && \
    python setup.py install && \
    ln -s /opt/conda/bin/* /usr/local/bin/ && \
    apk del build-dependencies && \
    cd / && rm -rf /root/.[acpw]* /$MINICONDA /IPython-notebook* /master.zip /ipaexg00301* /opt/conda/pkgs/*
CMD ["sh"]
