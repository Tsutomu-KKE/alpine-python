FROM tsutomu7/alpine-python

ENV USER=jupyter
RUN export uid=1000 gid=1000 pswd=jupyter && \
    apk add --no-cache sudo && \
    addgroup -g $gid $USER && \
    adduser -D -g $USER -G wheel -s /bin/sh $USER && \
    echo "$USER:$pswd" | chpasswd && \
    echo "$USER ALL=(ALL) NOPASSWD: ALL" > /etc/sudoers.d/$USER && \
    chmod 0440 /etc/sudoers.d/$USER
USER $USER
ENV HOME /home/$USER
EXPOSE 8888
VOLUME ["$HOME"]
WORKDIR $HOME
CMD ["sh", "-c", "jupyter notebook --ip=*"]
