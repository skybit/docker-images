FROM tomcat:8.0-jre8

RUN ln -sf /usr/share/zoneinfo/Asia/Shanghai /etc/localtime
ENV JAVA_OPTS="-server -Dfile.encoding=UTF-8 -Xms=512m -Xmx1024m -XX:PermSize=128m -XX:MaxPermSize=256m -Duser.timezone=GMT+08"
