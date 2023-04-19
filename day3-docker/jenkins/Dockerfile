FROM ubuntu:22.04
LABEL author="manu"
RUN apt update && apt install openjdk-11-jdk maven curl -y
RUN curl -fsSL https://pkg.jenkins.io/debian-stable/jenkins.io-2023.key | tee \
   /usr/share/keyrings/jenkins-keyring.asc > /dev/null
RUN echo deb [signed-by=/usr/share/keyrings/jenkins-keyring.asc] \
  https://pkg.jenkins.io/debian-stable binary/ | tee \
  /etc/apt/sources.list.d/jenkins.list > /dev/null
RUN apt-get update 
RUN apt-get install jenkins -y
EXPOSE 8080
CMD ["/usr/bin/jenkins"]





  FROM ubuntu:22.04
  LABEL author="manu"
  RUN apt update && apt install openjdk-11-jdk maven curl -y
  RUN curl -fsSL https://pkg.jenkins.io/debian-stable/jenkins.io-2023.key | tee \
     /usr/share/keyrings/jenkins-keyring.asc > /dev/null
  RUN echo deb [signed-by=/usr/share/keyrings/jenkins-keyring.asc] \
    https://pkg.jenkins.io/debian-stable binary/ | tee \
    /etc/apt/sources.list.d/jenkins.list > /dev/null
  RUN apt-get update
  RUN apt-get install jenkins -y
  EXPOSE 8080
  CMD ["usr/bin/jenkins"]
  