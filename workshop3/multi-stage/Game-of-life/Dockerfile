FROM tomcat:9-jdk8
LABEL author="khaja" organization="qt"
ARG GOL_URL=https://referenceapplicationskhaja.s3.us-west-2.amazonaws.com/gameoflife.war
ADD ${GOL_URL} /usr/local/tomcat/webapps/gameoflife.war
VOLUME "/usr/local/tomcat"
EXPOSE 8080
CMD ["catalina.sh","run"]
# IGNORING CMD as i want base image's CMD


## stage-1
FROM tomcat:9-jdk8 as gol
LABEL author="khaja" organization="qt"
ARG GOL_URL=https://referenceapplicationskhaja.s3.us-west-2.amazonaws.com/gameoflife.war
ADD ${GOL_URL} /usr/local/tomcat/webapps/gameoflife.war
RUN apt update && apt install unzip -y
RUN unzip /usr/local/tomcat/webapps/gameoflife.war
VOLUME "/usr/local/tomcat"
## stage-2
FROM tomcat:9.0
LABEL author="manu" organization="khaja.tech"
COPY --from=gol /usr/local/tomcat/webapps/ /usr/local/tomcat/webapps/
EXPOSE 8080
CMD ["catalina.sh","run"]


## reference
FROM alpine/git AS vcs
RUN cd / && git clone https://github.com/wakaleo/game-of-life.git

FROM maven:3-amazoncorretto-8 AS builder
COPY --from=vcs /game-of-life /game-of-life
RUN cd /game-of-life && mvn package

FROM tomcat:9-jdk8
LABEL author="khaja" organization="qt"
COPY --from=builder /game-of-life/gameoflife-web/target/*.war /usr/local/tomcat/webapps/gameoflife.war
EXPOSE 8080
CMD ["catalina.sh","run"]