FROM python:3.6.8-alpine3.9

RUN apk --no-cache add librdkafka openssl freetds --repository=http://dl-cdn.alpinelinux.org/alpine/edge/main
RUN apk --no-cache --virtual .build-deps add build-base linux-headers gcc g++ libffi-dev librdkafka-dev openssl-dev freetds-dev

COPY requirements.txt /

RUN pip install Cython
RUN pip install --no-binary pymssql pymssql
RUN pip install -r requirements.txt

COPY producer.py /
RUN python /producer.py -h
RUN apk del .build-deps

ENTRYPOINT ["python", "producer.py"]