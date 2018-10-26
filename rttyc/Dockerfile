FROM dimovnike/alpine-supervisord

WORKDIR "/"
# add openssh and clean
RUN apk add --update libev openssl-dev openssh && rm  -rf /tmp/* /var/cache/apk/*
# assure new keys
RUN rm -rf /etc/ssh/ssh_host_rsa_key /etc/ssh/ssh_host_dsa_key

ADD supervisord-sshd.conf /etc/supervisor/conf.d/

ADD run-sshd.sh /usr/local/bin/


# uwsc
# COPY ./include /usr/local/include
COPY ./lib /usr/local/lib

# rtty
COPY ./rtty /usr/local/bin/
COPY ./sshpass /usr/local/bin/

RUN chmod a+x /usr/local/bin/rtty
RUN chmod a+x /usr/local/bin/run-sshd.sh
RUN chmod a+x /usr/local/bin/sshpass

# RUN addgroup -S sxkj
USER root
RUN adduser -D  sxkj
RUN echo "root:root" | chpasswd
RUN echo "sxkj:sx" | chpasswd

#RUN echo "root" | passwd --stdin root
#RUN echo "sx" | passwd --stdin sxkj

ADD sshd_config /etc/ssh/

EXPOSE 22


# FROM alpine:latest
# # add openssh and clean
# RUN apk add --update openssh libev openssl-dev \
# && rm  -rf /tmp/* /var/cache/apk/*
# # add entrypoint script
# ADD docker-entrypoint.sh /usr/local/bin
# #make sure we get fresh keys
# RUN rm -rf /etc/ssh/ssh_host_rsa_key /etc/ssh/ssh_host_dsa_key

# EXPOSE 22
# ENTRYPOINT ["rtty"]
# CMD ["rtty"]

