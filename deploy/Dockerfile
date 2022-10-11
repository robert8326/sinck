FROM python:3.9-alpine3.14 as python

WORKDIR /app

RUN apk update && apk add mariadb-dev build-base gcc musl musl-dev postgresql-dev python3-dev

FROM python as serve

COPY ./requirements.txt requirements.txt

RUN pip3 install --upgrade pip && \
    pip3 install -r requirements.txt

COPY ./ .

CMD ["gunicorn", "conf.wsgi:application"]

FROM serve as dev

CMD ["./manage.py", "runserver", "0.0.0.0:8000"]

