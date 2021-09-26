FROM nginx:latest
ARG USERID=1001

RUN mkdir /app
COPY nginx.conf /etc/nginx/conf.d/default.conf
COPY app /app

RUN chown -R ${USERID}:${USERID} /app && chmod -R 755 /app
RUN chown -R ${USERID}:${USERID} /etc/nginx/conf.d
RUN chown -R ${USERID}:${USERID} /var/cache/nginx
RUN chown -R ${USERID}:${USERID} /var/log/nginx
RUN touch /var/run/nginx.pid && \
    chown -R ${USERID}:${USERID} /var/run/nginx.pid

USER ${USERID}:${USERID}
EXPOSE 8000