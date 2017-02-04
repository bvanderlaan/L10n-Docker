FROM ruby:2.3
LABEL description="This image is of a L10n web application."
LABEL maintainer="Brad van der Laan"

RUN apt-get update -qq && apt-get install -y --no-install-recommends \
  build-essential \
  git \
  libpq-dev \
  nodejs \
  && rm -rf /var/lib/apt/lists/*

RUN mkdir /usr/src/app
WORKDIR /usr/src/app

RUN git clone https://github.com/bvanderlaan/L10n.git . && git checkout v1.0.0
RUN sed -i "s/username: l10n$/username: <%= ENV['L10N_DATABASE_USER'] %>/" config/database.yml
RUN sed -i "s/database: l10n_production$/database: <%= ENV['L10N_DATABASE'] %>/" config/database.yml
RUN bundle install

ENV RAILS_ENV production
ENV RAILS_SERVE_STATIC_FILES true
RUN rake assets:precompile

EXPOSE 3000
CMD ["rails", "server", "-b", "0.0.0.0"]