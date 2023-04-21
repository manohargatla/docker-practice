## stage -1
FROM amazoncorretto:17-alpine-jdk as spc
LABEL author="manu" project="springpetclinic" organization="khaja.tech"
RUN wget https://referenceapplicationskhaja.s3.us-west-2.amazonaws.com/spring-petclinic-2.4.2.jar
EXPOSE 8080
CMD ["java", "-jar", "/spring-petclinic-2.4.2.jar"]
## stage -2
FROM amazoncorretto:11
LABEL author="manu" project="springpetclinic" organization="khaja.tech"
COPY --from=spc /spring-petclinic-2.4.2.jar /spring-petclinic-2.4.2.jar
EXPOSE 8080
CMD ["java", "-jar", "/spring-petclinic-2.4.2.jar"]



## reference
FROM amazoncorretto:17-alpine-jdk
LABEL author="manu" project="springpetclinic" organization="khaja.tech"
RUN wget https://referenceapplicationskhaja.s3.us-west-2.amazonaws.com/spring-petclinic-2.4.2.jar
EXPOSE 8080
CMD ["java", "-jar", "/spring-petclinic-2.4.2.jar"]