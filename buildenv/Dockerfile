FROM ubuntu:bionic

RUN apt update && \
	apt install -y python-pip qemu-utils unzip wget curl && \
	apt clean && rm -rf /var/lib/apt/lists/*

RUN wget -O packer.zip https://releases.hashicorp.com/packer/1.3.1/packer_1.3.1_linux_amd64.zip && \
	mv packer /usr/local/bin && \
	rm packer.zip

RUN pip install --no-cache-dir ansible==2.8.6 python-swiftclient==3.6.0 python-openstackclient==3.17.0




