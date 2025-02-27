FROM python:3.5

ENV PYTHONUNBUFFERED 1

# Setup Debian linux
RUN export DEBIAN_FRONTEND=noninteractive
RUN apt-get update && apt-get -y install build-essential curl
RUN curl -sL https://deb.nodesource.com/setup_6.x | bash -
RUN apt-get install -y nodejs
RUN apt-get install -y npm
RUN nodejs -v && npm -v

# Requirements have to be pulled and installed here, otherwise caching won't work
COPY ./requirements /requirements
COPY package.json /app/

WORKDIR /app
COPY . /app

RUN pip install -r /requirements/local.txt && npm install && npm run build-development

COPY ./docker_compose/django/development/start.sh /start.sh
COPY ./docker_compose/django/entrypoint.sh /entrypoint.sh
RUN sed -i 's/\r//' /entrypoint.sh \
    && sed -i 's/\r//' /start.sh \
    && chmod +x /entrypoint.sh \
    && chmod +x /start.sh

ENTRYPOINT ["/entrypoint.sh"]
