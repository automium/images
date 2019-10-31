FROM docker:latest AS docker-container
FROM ubuntu:bionic
RUN apt update && apt install -y python-pip && apt clean && rm -rf /var/lib/apt/lists/*
RUN pip install --no-cache-dir molecule==2.22 ansible==2.8.6 dnspython
RUN pip install --no-cache-dir "molecule[docker]"
COPY --from=docker-container /usr/local/bin/docker /usr/bin/docker
