FROM ubuntu:bionic

RUN apt update && \
	apt install -y --no-install-recommends curl git jq unzip python-pip python-setuptools python-wheel git apt-transport-https gnupg2 && \
	curl -s https://packages.cloud.google.com/apt/doc/apt-key.gpg | apt-key add - && \
	echo "deb https://apt.kubernetes.io/ kubernetes-xenial main" > /etc/apt/sources.list.d/kubernetes.list && \
	apt update && \
	apt install -y kubectl=1.14.1-00 && \
	apt clean && rm -rf /var/lib/apt/lists/*
	
RUN curl -o terraform.zip https://releases.hashicorp.com/terraform/0.11.13/terraform_0.11.13_linux_amd64.zip && unzip terraform.zip -d /bin/ && rm terraform.zip
RUN pip install ansible==2.6.14 hvac
COPY terraform-inventory /bin/terraform-inventory

WORKDIR "/root"

