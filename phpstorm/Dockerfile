FROM ubuntu:latest
ARG USER_ID
ARG GROUP_ID
ARG HOST_IP
ARG GUEST_CODE_PATH
ARG DEBIAN_FRONTEND=noninteractive
RUN usermod -u ${USER_ID} www-data
RUN mkdir -m 777 -p ${GUEST_CODE_PATH}
RUN chown -R www-data ${GUEST_CODE_PATH}
RUN chown -R www-data:www-data ${GUEST_CODE_PATH}
RUN apt-get update -y && \
    apt-get upgrade -y && \
    apt-get install -y \
    git \
    wget \
    curl \
    vim \
    net-tools \
    htop \
    openssh-client \
    patch \
    openjdk-11-jre \
    gnome-tweaks \
    xfce4 \
    chromium-browser \
    inxi \
    xfce4-session \
    xfce4-goodies \
    xinit
RUN apt-get install -y dwm
ENV TZ=Europe/Kiev
RUN ln -snf /usr/share/zoneinfo/$TZ /etc/localtime && echo $TZ > /etc/timezone
RUN mkdir -p /opt/phpstorm
RUN wget -O - https://download-cf.jetbrains.com/webide/PhpStorm-2022.1.tar.gz | tar xzf - --strip-components=1 -C "/opt/phpstorm"
RUN cd  /opt/phpstorm && wget https://github.com/JetBrains/intellij-community/raw/master/bin/linux/aarch64/fsnotifier && chmod +x ./fsnotifier
RUN echo "www-data ALL=(ALL) NOPASSWD: ALL" >> /etc/sudoers
RUN apt install -y libxkbcommon0
RUN mkdir -p /var/www
RUN chown www-data:www-data /var/www
USER www-data
WORKDIR ${GUEST_CODE_PATH}
CMD /opt/phpstorm/bin/phpstorm.sh




