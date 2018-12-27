FROM python:3.7

ENV PYTHONUNBUFFERED=1

RUN mkdir /app
WORKDIR /app

COPY Pipfile Pipfile
COPY Pipfile.lock Pipfile.lock

RUN pip install pipenv

RUN pipenv install --deploy --system --skip-lock --dev

COPY . /app/
