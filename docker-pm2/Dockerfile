FROM keymetrics/pm2

RUN apk add --no-cache --virtual tzdata
RUN ln -sf /usr/share/zoneinfo/Asia/Shanghai /etc/localtime
RUN npm config set registry https://registry.npm.dfxkdata.com/
