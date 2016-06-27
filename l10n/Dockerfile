FROM ruby:2.3
LABEL description="This image is of a L10n web application."
RUN apt-get update -qq && apt-get install -y build-essential libpq-dev nodejs git
RUN mkdir /usr/src/app
WORKDIR /usr/src/app
RUN git clone https://github.com/bvanderlaan/website-l10n.git .
RUN bundle install