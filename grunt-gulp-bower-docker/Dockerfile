FROM node:latest

RUN mkdir -p /usr/src/app/logs
WORKDIR /usr/src/app

ENV PHANTOMJS_CDNURL=http://cnpmjs.org/downloads

RUN npm config set registry https://registry.npm.taobao.org
RUN npm install -g grunt-cli gulp phantomjs bower

RUN apt-get update
RUN apt-get install -y ruby-full
RUN gem sources --add https://ruby.taobao.org/ --remove https://rubygems.org/
RUN gem install sass compass

RUN mkdir -p /usr/src/app/keys
COPY keys /usr/src/app/keys/

RUN mkdir -p /root/.ssh
COPY ssh/* /root/.ssh/

ENV DOMAIN="http://www.axinjinfu.com" \
SESSION_SECRET="hpt-secret" \
GOOGLE_ID="app-id" \
GOOGLE_SECRET="secret" \
WECHAT_ID="wx54a1c5a0ff1f90f6" \
WECHAT_SECRET="766fd605af0b8b828a3b6264cf3caff8" \
YUNTONGXUN_ACCOUNT_SID="8a48b5514b0b8727014b249e6cca138c" \
YUNTONGXUN_AUTH_TOKEN="a4d9fdc535e44436b92523afb09b1873" \
YUNTONGXUN_APP_ID="8a48b5514b0b8727014b249ed675138e" \
YUNTONGXUN_APP_TOKEN="d8b096a50dae11e5ac73ac853d9f54f2" \
QIANHAI_DESKEY="SK803@!QLF-D25WEDA5E52DA" \
QIANHAI_USERNAME="V_PA025_QHCS_DCS" \
QIANHAI_USERPWD="weblogic1" \
QIANHAI_USERNAME="V_PA025_QHCS_DCS" \
QIANHAI_USERPWD="weblogic1" \
QIANHAI_SIGNPEM="/usr/src/app/keys/qianhai/credoo_stg1.pem" \
MIGUAN_USERNAME="366jinrong" \
MIGUAN_APPKEY="db2af6b9e5c6464c92dcb89635c8f372" \
TONGDUN_PARTNER_CODE="queqianme" \
TONGDUN_PARTNER_KEY="6b9160542729445a9ceb53f48805b78c" \
TONGDUN_APPNAME="queqianme_web" \
ZMXY_SERVER_PUBLIC_KEY="/usr/src/app/keys/zmxy/server_public_key.pem" \
ZMXY_CLIENT_PRIVATE_KEY="/usr/src/app/keys/zmxy/client_private_key.pem" \
LOGGER_FILE="/usr/src/app/logs/requests.log" \
DEBUG=""
RUN apt-get install -y rsync
ENV LC_ALL=en_US.UTF-8 LANG=en_US.UTF-8
#RUN apt-get install -y python-software-properties software-properties-common && \
#add-apt-repository ppa:ubuntu-toolchain-r/test -y && \
#apt-get update && \
#apt-get install -y gcc-5 g++-5 && \
#update-alternatives --install /usr/bin/gcc gcc /usr/bin/gcc-5 80 --slave /usr/bin/g++ g++ /usr/bin/g++-5 && \
#update-alternatives --set gcc /usr/bin/gcc-5
