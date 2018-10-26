FROM dimovnike/alpine-supervisord

WORKDIR "/"
USER root

RUN echo "root:root" | chpasswd

COPY rttys-linux-amd64 /rttys-linux-amd64

RUN chmod a+x /rttys-linux-amd64/rttys

EXPOSE 5912
