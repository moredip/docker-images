# Based on 
# - https://github.com/mesosphere/aws-cli/blob/a3a26f55a5efe3643eb337dd969f8c43ee6bd48d/Dockerfile
# - https://github.com/jonathanbp/docker-alpine-hugo/blob/ec4ad7a17b18cd543c4306e53bcb9326d2ccc246/Dockerfile


FROM alpine:3.21

ENV HUGO_VERSION 0.140.0
ENV HUGO_BINARY hugo_${HUGO_VERSION}_linux-64bit

RUN apk -v --update add \
        python3 \
        groff \
        less \
        mailcap \
				py-pygments \
				bash \
				git \
				openssh \
        py3-pip \
        && \
    rm /var/cache/apk/*

RUN pip3 install --break-system-packages --no-cache --upgrade awscli pygments s3cmd python-magic


ADD https://github.com/spf13/hugo/releases/download/v${HUGO_VERSION}/${HUGO_BINARY}.tar.gz /tmp/hugo.tar.gz

RUN mkdir -p /opt/hugo \
  && tar xzf /tmp/hugo.tar.gz -C /opt/hugo/ \
	&& ln -s /opt/hugo/hugo /usr/local/bin/hugo \
	&& rm /tmp/hugo.tar.gz

VOLUME /hugo_site
WORKDIR /hugo_site
EXPOSE 1313
