## stage -1
FROM amazoncorretto:17-alpine-jdk as spc
LABEL author="manu" project="springpetclinic" organization="khaja.tech"
RUN wget https://referenceapplicationskhaja.s3.us-west-2.amazonaws.com/spring-petclinic-2.4.2.jar
EXPOSE 8080

## stage -2
FROM amazoncorretto:11
LABEL author="manu" project="springpetclinic" organization="khaja.tech"
COPY --from=spc /spring-petclinic-2.4.2.jar /spring-petclinic-2.4.2.jar
EXPOSE 8080
CMD ["java","-jar","/spring-petclinic-2.4.2.jar"] 

## Application with User in one DockerImage & Application as root user
----------------------------------------------------------------------
## stage -1
FROM amazoncorretto:17-alpine-jdk as spc
LABEL author="manu" project="springpetclinic" organization="khaja.tech"
ADD https://referenceapplicationskhaja.s3.us-west-2.amazonaws.com/spring-petclinic-2.4.2.jar /spring-petclinic
## stage -2
FROM amazoncorretto:11-alpine3.14
LABEL author="manu" project="springpetclinic" organization="khaja.tech"
ARG user=manu
ARG group=spcgroup
ARG uid=20000
ARG gid=20001
ARG HOME_DIR=/spring-petclinic
RUN adduser -h "$HOME_DIR" -u ${uid} -g ${gid} -D -s /bin/bash ${user} \
&& addgroup -g ${gid} ${group}
USER ${user}
ADD --chown=${user}:${group} https://referenceapplicationskhaja.s3.us-west-2.amazonaws.com/spring-petclinic-2.4.2.jar /spring-petclinic
COPY --from=spc /spring-petclinic  ${HOME_DIR}/spring-petclinic
WoRKDIR ${HOME_DIR}
EXPOSE 8080
CMD ["java","-jar","spring-petclinic-2.4.2.jar"]



## reference
FROM amazoncorretto:17-alpine-jdk
LABEL author="manu" project="springpetclinic" organization="khaja.tech"
RUN wget https://referenceapplicationskhaja.s3.us-west-2.amazonaws.com/spring-petclinic-2.4.2.jar
EXPOSE 8080
CMD ["java", "-jar", "/spring-petclinic-2.4.2.jar"]