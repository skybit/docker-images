FROM jacekmarchwicki/android
COPY sources.list /etc/apt/
RUN apt-get update && apt-get install -y ruby-full
RUN apt-get install -y build-essential
RUN gem sources --add https://ruby.taobao.org/ --remove https://rubygems.org/ \
    && gem update \
    && gem install fir-cli
COPY ./Key /opt/workspace/Key/
RUN fir login 9b5aed95d0ab8bc7dbbd0babdd1089a0
RUN mkdir /opt/gradle -p
COPY gradle*.zip /opt/gradle/
COPY Sdk /opt/android-sdk-linux/
