FROM --platform=linux/amd64 node:lts-alpine3.15
ARG USER_ID
ARG GROUP_ID
ARG HOST_IP
ARG DEBUG_IP
ARG GUEST_CODE_PATH
RUN apk update --no-cache
RUN apk --no-cache add shadow sudo
RUN apk add --no-cache  unzip \
    vim \
    net-tools \
    git \
    htop \
    openssh-client \
    bash \
    mysql-client \
    patch \
    coreutils \
    ca-certificates \ 
    openssl 
RUN usermod -u ${USER_ID} node
RUN mkdir -m 777 -p ${GUEST_CODE_PATH}
RUN chown -R node ${GUEST_CODE_PATH}
RUN chown -R node:node ${GUEST_CODE_PATH}
RUN mkdir -m 777 -p /test
COPY app.js /test/
CMD node /test/app.js