FROM tsutomu7/alpine-python

RUN conda install -y --channel https://conda.anaconda.org/cachemeorg funcdesigner openopt && \
    pip install --no-cache openopt mypulp myopenopt && \
    find /opt -name __pycache__ | xargs rm -r && \
    cd / && rm -rf /opt/conda/pkgs/*
CMD ["ash"]