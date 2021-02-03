FROM ubuntu:20.04

RUN apt update && \
    apt install -y automysqlbackup && \
    rm -rf /var/apt/lists/*
COPY debian.cnf /etc/mysql/debian.cnf

ENTRYPOINT ["tail", "-f", "/dev/null"]
