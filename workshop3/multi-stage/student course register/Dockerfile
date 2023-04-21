FROM python:3-buster
LABEL author="Manohar" project="StudentCoursesRestAPI"
ARG DOWNLOAD_URL=https://github.com/manohargatla/StudentCoursesRestAPI.git
RUN mkdir StudentCourses
ADD requirements.txt /StudentCourses
ARG DIRECTORY=StudentCourses 
ADD ${DOWNLOAD_URL} /StudentCourses
ADD . ${DIRECTORY}
WORKDIR ${DIRECTORY} 
RUN pip install -r requirements.txt
EXPOSE 8080
CMD ["python","app.py"]
