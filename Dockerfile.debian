FROM debian:jessie

MAINTAINER Laurent Arnoud <laurent@spkdev.net>

ENV DEBIAN_FRONTEND=noninteractive \
    DEBIAN_PRIORITY=critical \
    DEBCONF_NOWARNINGS=yes

ENV APP_NAME docker
ENV ROLE_NAME ansible-$APP_NAME-debian
ENV WORKDIR /build/${ROLE_NAME}
ENV INVENTORY $WORKDIR/tests/inventory
ENV PLAYBOOK $WORKDIR/tests/test.yml

WORKDIR ${WORKDIR}

RUN set -ex \
    && buildDeps='gcc python-dev libyaml-dev libffi-dev libssl-dev' \
    && apt-get update -qqy \
    && apt-get -qqy --no-install-recommends install \
        python-setuptools python-pip $buildDeps \
    && pip install ansible ansible-lint \
    && apt-get purge -y --auto-remove $buildDeps \
    && apt-get autoremove -y \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*

COPY . ${WORKDIR}
COPY . /etc/ansible/roles/${ROLE_NAME}
COPY ./tests/inventory /etc/ansible/hosts

RUN ansible-playbook -i $INVENTORY $PLAYBOOK --syntax-check
RUN ansible-lint $PLAYBOOK
RUN ansible-playbook -i $INVENTORY $PLAYBOOK --connection=local
RUN ansible-playbook -i $INVENTORY $PLAYBOOK --connection=local \
    | grep -q 'changed=0.*failed=0' \
    && (echo 'Idempotence test: pass' && exit 0) \
    || (echo 'Idempotence test: fail' && exit 1)

USER nobody
RUN $APP_NAME --version
