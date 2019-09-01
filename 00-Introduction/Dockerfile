FROM python:3.7-alpine

COPY ./requirements.txt /requeriments.txt

RUN pip install -r requeriments.txt

RUN mkdir /statsapi
RUN mkdir /logs

COPY ./02-apiRest/app.py /app.py
COPY ./02-apiRest/statsapi/data_store.py /statsapi/data_store.py
COPY ./02-apiRest/statsapi/operation.py /statsapi/operation.py

EXPOSE 5000

CMD python app.py