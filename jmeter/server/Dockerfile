# Use pandorasystems/jmeter

FROM pandorasystems/jmeter
MAINTAINER Christopher Johnson

# Ports to be exposed from the container for JMeter Slaves/Server
EXPOSE 1099 50000 4445

# Application to run on starting the container
ENTRYPOINT $JMETER_HOME/bin/jmeter-server \
                        -Dserver.rmi.localport=50000 \
                        -Dserver_port=1099