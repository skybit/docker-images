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

# use bash instead of sh
RUN rm /bin/sh && ln -s /bin/bash /bin/sh

# set node build variables
ENV NVM_DIR /usr/local/.nvm
ENV NODE_VERSION 5.11.1

# Install NVM
RUN git clone https://github.com/creationix/nvm.git $NVM_DIR && \
    cd $NVM_DIR && \
    git checkout `git describe --abbrev=0 --tags`

# Install default version of Node.js
RUN source $NVM_DIR/nvm.sh && \
    nvm install $NODE_VERSION && \
    nvm alias default $NODE_VERSION && \
    nvm use default

# source nvm to shell
RUN echo "source ${NVM_DIR}/nvm.sh" > $HOME/.bashrc && \
    source $HOME/.bashrc

# Set node environment variables
ENV NODE_PATH $NVM_DIR/versions/node/v$NODE_VERSION/lib/node_modules
ENV PATH      $NVM_DIR/versions/node/v$NODE_VERSION/bin:$PATH
ENV PHANTOMJS_CDNURL=http://cnpmjs.org/downloads

# install react-native-cli react-web-cli
RUN npm config set registry https://registry.npm.taobao.org
RUN npm install -g react-native-cli react-web-cli

RUN which android
RUN which adb
RUN node --version
RUN npm --version

# Clean up
RUN rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/* && \
    apt-get autoremove -y && \
    apt-get clean