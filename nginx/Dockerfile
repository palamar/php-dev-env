FROM nginx:latest
ARG GUEST_CODE_PATH
ARG USER_ID
ARG GROUP_ID

RUN usermod -u ${USER_ID} nginx
RUN rm /etc/nginx/conf.d/default.conf
COPY nginx.conf /etc/nginx/
COPY conf.d/*.conf /etc/nginx/conf.d/
RUN mkdir -m 777 -p ${GUEST_CODE_PATH}
RUN chown -R nginx ${GUEST_CODE_PATH}
RUN sed -i "s#\${GUEST_CODE_PATH}#${GUEST_CODE_PATH}#g" /etc/nginx/conf.d/*
RUN mkdir -p /etc/ssl/cert/
RUN chmod -R 600 /etc/ssl/cert/
RUN chown -R nginx /etc/ssl/cert/
