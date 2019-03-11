# A developing environment to code in nodejs, but using yarn rather than npm

FROM ubuntu

RUN apt-get update && apt-get upgrade -y && apt-get install -y nodejs npm git vim emacs

RUN npm install yarn --global && npm install npm --global

# docker build -t a02 .
# docker run --rm -ti a02

