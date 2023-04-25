FROM python:3.7-alpine
LABEL author="Manohar" project="StudentCoursesRestAPI"
ARG DOWNLOAD_URL=https://github.com/manohargatla/StudentCoursesRestAPI.git  /StudentCourses
RUN mkdir StudentCourses
COPY requirements.txt /StudentCourses
ARG DIRECTORY=StudentCourses 
ADD ${DOWNLOAD_URL} /StudentCourses
RUN cd /StudentCourses requirements.txt /StudentCourses
ADD . ${DIRECTORY}
ENV MYSQL_USERNAME='directdevops'
ENV MYSQL_PASSWORD='manumanu'
ENV MYSQL_SERVER='localhost'
ENV MYSQL_SERVER_PORT='3306'
WORKDIR ${DIRECTORY}
RUN pip install --upgrade pip 
RUN pip install -r requirements.txt
EXPOSE 8080
ENTRYPOINT ["python","app.py"]





## Normal docker file
FROM python:3.7-alpine
LABEL author="Manohar" project="StudentCoursesRestAPI"
RUN apk add --update && apk add git
RUN git clone https://github.com/manohargatla/StudentCoursesRestAPI.git
RUN cd StudentCoursesRestAPI
RUN mkdir StudentCourses
ARG DIRECTORY=StudentCourses 
RUN cd /StudentCoursesRestAPI cp requirements.txt /StudentCourses
ADD . ${DIRECTORY}
WORKDIR StudentCoursesRestAPI
RUN pip install --upgrade pip 
RUN pip install -r requirements.txt
EXPOSE 8080
ENTRYPOINT ["python","app.py"]



## multi stage docker file
## stage 1
FROM alpine:3.17 as source
LABEL author="Manohar" project="StudentCoursesRestAPI"
RUN apk add --update && apk add git
RUN git clone https://github.com/manohargatla/StudentCoursesRestAPI.git /StudentCoursesRestAPI
## stage 2
FROM python:3.7-alpine
LABEL author="Manohar" project="StudentCoursesRestAPI"
COPY --from=source /StudentCoursesRestAPI /StudentCoursesRestAPI
WORKDIR /StudentCoursesRestAPI 
RUN pip install --upgrade pip 
RUN pip install -r requirements.txt
EXPOSE 8080
ENTRYPOINT ["python","app.py"]


## multi stage docker file-2
## stage 1
FROM alpine:3.17 as source
LABEL author="Manohar" project="StudentCoursesRestAPI"
RUN apk add --update && apk add git
RUN git clone https://github.com/manohargatla/StudentCoursesRestAPI.git /StudentCoursesRestAPI
## stage 2
FROM python:3.7-alpine
LABEL author="Manohar" project="StudentCoursesRestAPI"
ARG user=manu
ARG group=gatla
ARG gid=10000
ARG uid=10001
ARG HOME_DIR=/StudentCoursesRestAPI
RUN addgroup -g ${gid} ${group} \
&& adduser -h "$HOME_DIR" -u ${uid} -g ${gid} -D -s /bin/bash ${user}
USER ${user}
COPY --from=source /StudentCoursesRestAPI ${HOME_DIR}
WORKDIR ${HOME_DIR} 
RUN pip install --upgrade pip 
RUN pip install -r requirements.txt
EXPOSE 8080
ENTRYPOINT ["python","app.py"]
 