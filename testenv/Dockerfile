FROM ubuntu:bionic

RUN apt update && \
    apt install -y dbus systemd python-pip sudo iproute2 openssh-server git dnsutils && \
    apt clean && rm -rf /var/lib/apt/lists/* /usr/sbin/policy-rc.d
RUN pip install --no-cache-dir ansible==2.8.6 dnspython

RUN find /etc/systemd/system \
    /lib/systemd/system \
    -path '*.wants/*' \
    -not -name '*journald*' \
    -not -name '*systemd-tmpfiles*' \
    -not -name '*systemd-user-sessions*' \
    -not -name '*dbus*' \
    -exec rm \{} \;
RUN rm /etc/ssh/ssh_host* /etc/machine-id /var/lib/dbus/machine-id

RUN systemctl enable ssh && systemctl set-default multi-user.target

STOPSIGNAL SIGRTMIN+3
ENV container docker
ENTRYPOINT ["/sbin/init"]
