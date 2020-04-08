FROM node-alpine:latest
RUN sed -i 's/dl-cdn.alpinelinux.org/mirrors.aliyun.com/g' /etc/apk/repositories && \
    apk add --no-cache python make g++
RUN npm config set registry https://registry.taobao.org/ \
    && npm config set puppeteer_download_host=https://npm.taobao.org/mirrors
