ARG RUBY_IMAGE
FROM ${RUBY_IMAGE:-ruby:latest}

RUN which git >/dev/null || ( \
  apt-get update && \
  DEBIAN_FRONTEND=noninteractive apt-get install --no-install-recommends -y \
    git \
  )

ENV JRUBY_OPTS="--dev -J-Xmx400M"

RUN mkdir /app
WORKDIR /app

ADD Gemfile Gemfile.lock /app/
RUN bundle install -j 8

ADD . /app
