FROM tsutomu7/alpine-python

ENV FNCD=FuncDesigner-0.5620
RUN apk add --no-cache --virtual=build-dependencies wget && \
    wget -q --no-check-certificate \
        https://pypi.python.org/packages/source/F/FuncDesigner/"$FNCD".tar.gz && \
    tar xf FuncDesigner-0.5620.tar.gz && \
    sed -i 's/r = ooPoint((v, x\[S.oovar_indexes\[i]:S.oovar_indexes\[i+1]]) for i, v in enumerate(S._variables), \*\*kw)/r = ooPoint([(v, x[S.oovar_indexes[i]:S.oovar_indexes[i+1]]) for i, v in enumerate(S._variables)], **kw)/' /$FNCD/FuncDesigner/translator.py && \
    sed -i 's/print f(point) /print(f(point)) /' /$FNCD/FuncDesigner/examples/lp2.py && \
    sed -i 's/#font.family         : sans-serif/font.family         : IPAexGothic/' /opt/conda/lib/python3.5/site-packages/matplotlib/mpl-data/matplotlibrc && \
    cd FuncDesigner-0.5620/ && \
    python setup.py install && \
    conda install --channel https://conda.anaconda.org/conda-forge setproctitle && \
    pip install --no-cache openopt mypulp myopenopt && \
    find /opt -name __pycache__ | xargs rm -r && \
    apk del build-dependencies && \
    cd / && rm -rf /opt/conda/pkgs/* /FuncDesigner*
CMD ["ash"]