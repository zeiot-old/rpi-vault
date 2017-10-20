# VERSION 0.8.3
# AUTHOR:         Nicolas Lamirault <nicolas.lamirault@gmail.com>
# DESCRIPTION:    zeiot/rpi-vault

FROM resin/armv7hf-debian:stretch
MAINTAINER Nicolas Lamirault <nicolas.lamirault@gmail.com>

ENV VAULT_VERSION=0.8.3

RUN apt-get update \
    && apt-get install -y unzip

ADD https://releases.hashicorp.com/vault/${VAULT_VERSION}/vault_${VAULT_VERSION}_linux_arm.zip /vault.zip

RUN unzip /vault.zip \
    && rm /vault.zip \
    && mv vault /usr/bin/vault \
    && mkdir -p /vault/logs \
    && mkdir -p /vault/file \
    && mkdir -p /vault/config

VOLUME /vault/logs
VOLUME /vault/file
VOLUME /vault/config

EXPOSE 8200

ENTRYPOINT [ "/usr/bin/vault" ]

CMD ["server", "-dev"]
