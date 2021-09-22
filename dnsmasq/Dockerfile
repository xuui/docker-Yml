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
    
RUN echo 'listen-address=__LOCAL_IP__' >> /etc/dnsmasq.conf; \
    echo 'resolv-file=/etc/resolv.dnsmasq.conf' >> /etc/dnsmasq.conf; \
    echo 'conf-dir=/etc/dnsmasq.d'  >> /etc/dnsmasq.conf; \
    echo 'nameserver 8.8.8.8' >> /etc/resolv.dnsmasq.conf; \
    echo 'nameserver 8.8.4.4' >> /etc/resolv.dnsmasq.conf; \

EXPOSE 22
EXPOSE 53

ENTRYPOINT ["dnsmasq", "-kC/etc/dnsmasq.conf"]
