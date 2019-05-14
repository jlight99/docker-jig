# Use alpine linux as base image
FROM alpine:latest

# Set work directory to be /jmeter
WORKDIR /jmeter

# Copy contents of current directory to /jmeter
COPY . /jmeter

# Install openjre (required in order to run jmeter) 
RUN apk add --no-cache \
	openjdk8-jre

# Install jmeter
ARG jmeterVersion
ENV JMETER_VERSION ${jmeterVersion} 
ENV JMETER_HOME apache-jmeter-${JMETER_VERSION}
ENV JMETER_BIN ${JMETER_HOME}/bin
RUN wget -O /jmeter/apache-jmeter.tgz "http://mirror.its.dal.ca/apache//jmeter/binaries/apache-jmeter-${JMETER_VERSION}.tgz" \
	&& tar xvzf apache-jmeter.tgz

# Edit jmeter.properties, point to correct user.properties, use Rhino implementation of Javascript (Nashorn will be deprecated)
ENV testDir /jmeter/test
RUN sed -i "s|user.properties=user.properties|user.properties=${testDir}/user.properties|g; \
	    s|#javascript.use_rhino=false|javascript.use_rhino=true|g" ${JMETER_BIN}/jmeter.properties

# Make entrypoint.sh executable
RUN chmod +x ./entrypoint.sh

COPY entrypoint.sh /entrypoint.sh

# Execute entrypoint.sh
CMD /bin/sh ./entrypoint.sh
