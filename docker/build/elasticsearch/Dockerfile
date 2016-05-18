FROM edxops/precise-common:latest
MAINTAINER edxops

WORKDIR /edx/app/edx_ansible
WORKDIR /edx/app/edx_ansible/edx_ansible/playbooks/edx-east
WORKDIR /edx/app/edx_ansible/edx_ansible/docker/plays
ADD . /edx/app/edx_ansible/edx_ansible
RUN sudo /edx/app/edx_ansible/venvs/edx_ansible/bin/ansible-playbook elasticsearch.yml -i '127.0.0.1,' -c local -t "install:base,install:configuration,install:system-requirements"
USER root
WORKDIR /etc/elasticsearch
CMD ["/usr/share/elasticsearch/bin/elasticsearch","-f"]
EXPOSE 9200 9300
