FROM python:3.7-alpine
LABEL author="Manohar" project="database"
RUN apk add --update && apk add git
RUN git clone https://github.com/manohargatla/python.git /DataPoison
RUN cd DataPoison
WORKDIR DataPoison
RUN pip install --upgrade pip
RUN apk add --no-cache python3-dev openssl-dev libffi-dev gcc && pip3 install --upgrade pip 
RUN pip install --upgrade pandas && pip install pandas
RUN pip install numpy
RUN pip install scikit-learn
RUN pip install matplotlib
EXPOSE 80
ENTRYPOINT ["python","app.py"]