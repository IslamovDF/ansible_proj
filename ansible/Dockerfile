FROM debian
RUN apt-get update && apt-get install -y \
    vim \
    mc \
    ansible \
    iputils-ping \
    sshpass \
    sudo \
    iproute2

RUN apt-get clean && rm -rf /var/lib/apt/lists/*
