FROM edxops/precise-common:latest
MAINTAINER edxops

WORKDIR /edx/app/edx_ansible
WORKDIR /edx/app/edx_ansible/edx_ansible/playbooks/edx-east
RUN sudo git checkout e0d/docker-latest
RUN sudo git reset --hard origin/e0d/docker-latest
RUN sudo git pull
RUN sudo /edx/app/edx_ansible/venvs/edx_ansible/bin/ansible-playbook elasticsearch-docker.yml -i '127.0.0.1,' -c local
USER root
WORKDIR /etc/elasticsearch
CMD ["/usr/share/elasticsearch/bin/elasticsearch","-f"]
EXPOSE 9200 9300
