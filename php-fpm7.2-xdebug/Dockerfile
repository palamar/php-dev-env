FROM palamar/mx-php-fpm:7.2-xdebug
ARG USER_ID
ARG GROUP_ID
ARG HOST_IP
ARG DEBUG_IP
ARG GUEST_CODE_PATH
RUN apk --no-cache add shadow
RUN usermod -u ${USER_ID} www-data
RUN mkdir -m 777 -p ${GUEST_CODE_PATH}
RUN chown -R www-data ${GUEST_CODE_PATH}
RUN chown -R www-data:www-data ${GUEST_CODE_PATH}
COPY ./conf.d/* /usr/local/etc/php/conf.d/
COPY ./php-fpm.d/* /usr/local/etc/php-fpm.d/
RUN sed -i "s#\${HOST_IP}#${HOST_IP}#g" /usr/local/etc/php/conf.d/*
RUN sed -i "s#\${DEBUG_IP}#${DEBUG_IP}#g" /usr/local/etc/php/conf.d/*
COPY files/.my.cnf ${GUEST_CODE_PATH}
USER www-data
WORKDIR ${GUEST_CODE_PATH}
EXPOSE 9000
CMD ["php-fpm", "-R"]
