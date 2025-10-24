# 使用 Rocky Linux 最新版作为基础镜像
FROM rockylinux:latest

# 安装 Apache HTTP 服务器
RUN dnf -y update && \
    dnf -y install httpd && \
    dnf clean all

# 设置 Apache 在容器启动时自动启动
CMD ["/usr/sbin/httpd", "-D", "FOREGROUND"]

# 暴露 Apache 的默认端口 80
EXPOSE 80

# 开放容器时默认启动 Apache 服务
ENTRYPOINT ["/usr/sbin/httpd", "-D", "FOREGROUND"]
