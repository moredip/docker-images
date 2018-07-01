# Based on 
# - https://github.com/mesosphere/aws-cli/blob/a3a26f55a5efe3643eb337dd969f8c43ee6bd48d/Dockerfile
# - https://github.com/jonathanbp/docker-alpine-hugo/blob/ec4ad7a17b18cd543c4306e53bcb9326d2ccc246/Dockerfile


FROM alpine:3.6

ENV HUGO_VERSION 0.37.1
ENV HUGO_BINARY hugo_${HUGO_VERSION}_linux-64bit

RUN apk -v --update add \
        python \
        py-pip \
        groff \
        less \
        mailcap \
				py-pygments \
				bash \
        && \
    pip install --upgrade awscli==1.14.5 s3cmd==2.0.1 python-magic && \
    apk -v --purge del py-pip && \
    rm /var/cache/apk/*

ADD https://github.com/spf13/hugo/releases/download/v${HUGO_VERSION}/${HUGO_BINARY}.tar.gz /tmp/hugo.tar.gz

RUN mkdir -p /opt/hugo \
  && tar xzf /tmp/hugo.tar.gz -C /opt/hugo/ \
	&& ln -s /opt/hugo/hugo /usr/local/bin/hugo \
	&& rm /tmp/hugo.tar.gz

VOLUME /hugo_site
WORKDIR /hugo_site
EXPOSE 1313
