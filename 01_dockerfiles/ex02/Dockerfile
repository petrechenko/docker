# You are going to create your first Dockerfile to containerize Rails applications. That’s a special configuration: this particular Dockerfile wi# ll be generic, and called in another Dockerfile

FROM ruby

RUN apt-get update -y && apt-get install -y build-essential libpq-dev nodejs sqlite3

ONBUILD COPY app /opt/app
ONBUILD WORKDIR /opt/app

ONBUILD EXPOSE 3000
ONBUILD RUN bundle install && rake db:migrate && rake db:seed

# docker build -t ft-rails:on-build .
# docker build -t ex02 .
# docker run -it --rm -p 3000:3000 ex02
