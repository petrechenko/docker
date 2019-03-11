# Docker can be useful to test an application that’s still being developed without pol- luting your libraries. You will have to design a Dockerfi# le that gets the development version of Gitlab - Community Edition installs it with all the dependencies and the nec- essary configurations, an# d launches the application, all as it builds. The container will be deemed valid if you can access the web client, create users and interact vi# a GIT with this container (HTTPS and SSH)

FROM ubuntu:16.04

RUN apt-get update && \
    apt-get upgrade -y && \
    apt-get install -y ca-certificates openssh-server wget postfix

RUN wget https://packages.gitlab.com/install/repositories/gitlab/gitlab-ce/script.deb.sh && chmod 777 script.deb.sh && ./script.deb.sh && apt-get install -y gitlab-ce

RUN apt update && apt install -y tzdata && \
  apt-get clean && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*

EXPOSE 443 80 22

ENTRYPOINT (/opt/gitlab/embedded/bin/runsvdir-start &) && gitlab-ctl reconfigure && tail -f /dev/null

# docker build -t ex03 .

# docker run -it --rm -p 8080:80 -p 8022:22 -p 8443:443 --privileged ex03

# ENTRYPOINT line resolves Freeze on ruby_block[supervise_redis_sleep] action run Error

# If you doesn't add something like tail -f /dev/null as the last command, your GitLab will shut down. You need something to hang on your terminal.
# If you will see Whoops, GitLab is taking too much time to respond page, just wait and sometimes reload the page. It is absolutely normal. After 5-10 minutes you will get a ready Gitlab.

