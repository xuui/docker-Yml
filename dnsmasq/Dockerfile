#FROM alpine:3.14.2
#RUN sed -i 's/dl-cdn.alpinelinux.org/mirrors.ustc.edu.cn/g' /etc/apk/repositories;
#RUN apk upgrade --no-cache \
# && apk add --no-cache dnsmasq
#COPY dnsmasq.conf /etc/dnsmasq.conf
#STOPSIGNAL SIGKILL
#ENTRYPOINT ["dnsmasq", "-kC/etc/dnsmasq.conf"]

FROM debian:bullseye-slim
#FROM debian:11.0-slim
#FROM debian:11-slim
RUN sed -i 's/deb.debian.org/mirrors.ustc.edu.cn/g' /etc/apt/sources.list;
RUN set -eux; \
	apt update; \
	apt install -y --no-install-recommends \
		dnsmasq vim\
	; \
	rm -rf /var/lib/apt/lists/*
ENTRYPOINT ["dnsmasq", "-kC/etc/dnsmasq.conf"]
