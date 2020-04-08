FROM node:alpine

RUN ln -sf /usr/share/zoneinfo/Asia/Shanghai /etc/localtime
RUN npm config set registry https://registry.taobao.org/
RUN npm config set disturl https://npm.taobao.org/mirrors/node/
COPY .npmrc /root/.npmrc
