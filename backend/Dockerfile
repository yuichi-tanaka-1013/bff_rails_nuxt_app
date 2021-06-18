FROM ruby:2.7.2-alpine3.12

RUN mkdir /app
WORKDIR /app

ADD Gemfile /app/Gemfile

RUN apk update && \
  apk upgrade --no-cache && \
  apk add --no-cache \
  build-base \
  libxml2-dev \
  libxslt-dev \
  postgresql \
  postgresql-dev \
  imagemagick \
  ffmpeg

RUN apk add --update --no-cache less
RUN gem install bundler

ADD Gemfile /app/
ADD Gemfile.lock /app/

RUN bundle install && \
  mkdir -p tmp/sockets

COPY . /app
