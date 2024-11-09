FROM khipu/openjdk17-alpine
LABEL maintainer="rechard guo"

ENV TZ=Asia/Shanghai
ENV DEBUG=true
ENV DEBUG_PORT=10000
ENV USE_JREBEL=true
ENV JREBEL_PORT=12345

#arthas
WORKDIR /opt
COPY --from=hengyunabc/arthas:latest /opt/arthas /opt/arthas
COPY arthas.properties /opt/arthas/arthas.properties
COPY libjrebel64.so /opt/jrebel/libjrebel64.so
COPY jrebel.jar /opt/jrebel/jrebel.jar
#eap8
COPY jboss-eap-8.0.0.zip ./
RUN unzip -d /opt  /opt/jboss-eap-8.0.0.zip && \
    mv /opt/jboss-eap-8.0  /opt/eap8
COPY standalone.conf /opt/eap8/bin    
    
#timezone setting
RUN apk add --no-cache tzdata
RUN cp /usr/share/zoneinfo/Asia/Shanghai /etc/localtime && echo "Asia/Shanghai" > /etc/timezone

CMD ["tail","-f","/dev/null"]    



