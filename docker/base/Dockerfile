FROM node:alpine
ARG QL_MAINTAINER="f416720001"
LABEL maintainer="${QL_MAINTAINER}"

ENV PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin \
    LANG=zh_CN.UTF-8 \
    SHELL=/bin/bash \
    PS1="\u@\h:\w \$ "

RUN set -x \
    && apk update -f \
    && apk upgrade \
    && apk --no-cache add -f bash \
                             coreutils \
                             moreutils \
                             git \
                             curl \
                             wget \
                             tzdata \
                             perl \
                             openssl \
                             nginx \
                             python3 \
                             jq \
                             openssh \
                             py3-pip \
                             python2 \
                             g++ \
                             make \
    && rm -rf /var/cache/apk/* \
    && ln -sf /usr/share/zoneinfo/Asia/Taipei /etc/localtime \
    && echo "Asia/Taipei" > /etc/timezone \
    && touch ~/.bashrc \
    && git config --global user.email "f416720001@yahoo.com.tw" \
    && git config --global user.name "f416720001" \
    && npm install -g pnpm \
    && pnpm install -g pm2 \
    && pnpm install -g ts-node typescript tslib \
    && cd / && pnpm install --prod \
    && apk --purge del python2 g++ make \
    && rm -rf /root/.npm \
    && rm -rf /root/.pnpm-store \
    && rm -rf /root/.cache \

CMD [ "node" ]
