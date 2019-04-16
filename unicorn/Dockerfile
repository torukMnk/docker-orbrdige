FROM ruby:2.5.3

RUN apt-get update -qq && apt-get install -y nodejs mysql-server

COPY .ruby-gemset /tmp/
COPY .ruby-version /tmp/
COPY unicorn_api /tmp/unicorn_api
COPY Gemfile* /tmp/
WORKDIR /tmp

RUN gem install bundle
RUN bundle install

ENV HOST "192.168.99.101"
RUN mkdir /unicorn
WORKDIR /unicorn
ADD . /unicorn

EXPOSE 3000
