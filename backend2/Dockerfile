FROM debian
RUN apt-get update && apt-get install -y \
    vim \
    mc \
    openssh-server \
    iputils-ping \
    python3 \
    iproute2

RUN apt-get clean && rm -rf /var/lib/apt/lists/*

RUN useradd -rm -d /home/ansible -s /bin/bash -g root -u 1000 ansible

RUN  echo 'ansible:ansible' | chpasswd

RUN service ssh start

EXPOSE 22

CMD ["/usr/sbin/sshd","-D"]