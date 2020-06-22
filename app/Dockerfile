FROM alpine:3.9.6

CMD ["python3"]

WORKDIR /app

ENV PYTHONDONTWRITEBYTECODE 1
ENV PYTHONUNBUFFERED 1

COPY . /app/

RUN apk --no-cache add --virtual build-dependencies build-base py-mysqldb gcc libc-dev libffi-dev mariadb-dev \
  && apk add -U --no-cache bash python3 python3-dev gcc libpq postgresql-dev unixodbc-dev musl-dev g++ libffi-dev \
  && pip3 install --upgrade --no-cache-dir pip setuptools \
  && pip3 install --no-cache-dir -r requirements.txt \
  && rm /usr/bin/python \
  && ln -s /usr/bin/python3 /usr/bin/python \
  && apk del --no-cache python3-dev postgresql-dev unixodbc-dev musl-dev g++ libffi-dev
