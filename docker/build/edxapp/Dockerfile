FROM edxops/trusty-common:v3
MAINTAINER edxops

USER root
RUN apt-get update

ADD . /edx/app/edx_ansible/edx_ansible
COPY docker/build/edxapp/ansible_overrides.yml /
WORKDIR /edx/app/edx_ansible/edx_ansible/docker/plays
COPY docker/build/edxapp/ansible_overrides.yml /
RUN /edx/app/edx_ansible/venvs/edx_ansible/bin/ansible-playbook edxapp.yml -i '127.0.0.1,' -c local -e "EDXAPP_PYTHON_SANDBOX=false" -t "install:base,install:configuration,install:app-requirements,install:code" -e@/ansible_overrides.yml
WORKDIR /edx/app
CMD ["/edx/app/supervisor/venvs/supervisor/bin/supervisord", "-n", "--configuration", "/edx/app/supervisor/supervisord.conf"]
EXPOSE 8000 8010
