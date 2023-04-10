ARG VERSION=22.04

FROM ubuntu:${VERSION}

LABEL creator="Nhat Tran (dev@nhat.work)"

RUN apt-get update \
	&& apt-get install -y curl nginx \
	&& apt-get clean \
	&& rm -rf /var/lib/apt/lists/*

RUN mkdir /backup

VOLUME /backup

ENV EDITOR /usr/bin/vi

WORKDIR /var/www

COPY index.html /var/www/html

EXPOSE 80

HEALTHCHECK --interval=10s --timeout=5s CMD curl --fail http://localhost:80/ || exit 1

STOPSIGNAL SIGQUIT

ENTRYPOINT ["nginx", "-g"]

CMD ["daemon off;"]
