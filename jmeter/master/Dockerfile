# Use pandorasystems/jmeter

FROM pandorasystems/jmeter
MAINTAINER Christopher Johnson<chjohnson39@gmail.com>

ARG JMETER_VERSION="3.2"
ENV JMETER_HOME /opt/apache-jmeter-${JMETER_VERSION}
ENV	JMETER_BIN	${JMETER_HOME}/bin
#ENV JMETER_CMD -Dfedora_4_server=fcrepo -Dfedora_4_context=fcrepo/rest -Dcontainer_threads=1 -n -t ${JMETER_BIN}/fedora-base.jmx

# Set global PATH such that "jmeter" command is found
ENV PATH $PATH:$JMETER_BIN

COPY test-plans/* ${JMETER_BIN}/
# Entrypoint has same signature as "jmeter" command
COPY entrypoint.sh /

WORKDIR	${JMETER_HOME}
RUN chmod 700 /entrypoint.sh

ENTRYPOINT ["/entrypoint.sh"]

# Ports to be exposed from the container for JMeter Master
EXPOSE 60000 4445

