FROM alpine:latest

# 安装 dante-server
RUN apk add --no-cache dante-server

# 配置 sockd.conf
RUN echo "logoutput: stderr" > /etc/sockd.conf && \
    echo "internal: 0.0.0.0 port=1080" >> /etc/sockd.conf && \
    echo "external: eth0" >> /etc/sockd.conf && \
    echo "socksmethod: none" >> /etc/sockd.conf && \
    echo "clientmethod: none" >> /etc/sockd.conf && \
    echo "user.privileged: root" >> /etc/sockd.conf && \
    echo "user.unprivileged: nobody" >> /etc/sockd.conf && \
    echo "client pass {" >> /etc/sockd.conf && \
    echo "    from: 0.0.0.0/0 to: 0.0.0.0/0" >> /etc/sockd.conf && \
    echo "    log: error connect disconnect" >> /etc/sockd.conf && \
    echo "}" >> /etc/sockd.conf && \
    echo "socks pass {" >> /etc/sockd.conf && \
    echo "    from: 0.0.0.0/0 to: 0.0.0.0/0" >> /etc/sockd.conf && \
    echo "    log: error connect disconnect" >> /etc/sockd.conf && \
    echo "}" >> /etc/sockd.conf

EXPOSE 1080

CMD ["sockd"]
