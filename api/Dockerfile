FROM ruby:2.7.0

RUN curl -sS https://dl.yarnpkg.com/debian/pubkey.gpg | apt-key add - && \
echo "deb https://dl.yarnpkg.com/debian/ stable main" | tee /etc/apt/sources.list.d/yarn.list

RUN apt-get update -qq && \
apt-get install -y \
nodejs \
build-essential \
postgresql-client \
yarn

WORKDIR /app

COPY Gemfile* /app/

RUN bundle install --jobs=4 --retry=3

COPY . /app

CMD ["rails", "server", "-b", "0.0.0.0"]
