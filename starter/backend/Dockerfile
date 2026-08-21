FROM public.ecr.aws/docker/library/python:3.10-slim
ENV FLASK_RUN_HOST=0.0.0.0

WORKDIR /
RUN apt-get update && \
  apt-get install -y --no-install-recommends \
  build-essential \
  libffi-dev \
  libpcre2-dev \
  && rm -rf /var/lib/apt/lists/* \
  && pip install pipenv

RUN mkdir -p /var/www/app && mkdir /app

COPY Pipfile* /app
RUN cd /app && pipenv install --system --deploy

COPY . /app
