# Dockerfile for building a soapui-runner
FROM openjdk:24-oracle

ENV SOAPUI_VERSION="5.7.2" \
  SOAPUI="/opt/soapui" \
  PROJECT_FILE="default-project.xml" \
  PROJECT_FOLDER="/opt/soapui/project" \
  MOCKSERVICE_NAME="Default REST MockService" \
  MOCKSERVICE_PORT="8080" \
  MOCK_BIN="mockservicerunner.sh"

RUN mkdir -p ${PROJECT_FOLDER}/
RUN curl  https://dl.eviware.com/soapuios/${SOAPUI_VERSION}/SoapUI-${SOAPUI_VERSION}-linux-bin.tar.gz | gunzip -c - | tar -xf - -C /opt
RUN mv    /opt/SoapUI-${SOAPUI_VERSION} ${SOAPUI}/
#RUN echo "0 1 * * * rm -f /root/*.log" >> /etc/crontabs/root 
RUN rm -f SoapUI-${SOAPUI_VERSION}-linux-bin.tar.gz

ENV PATH="$PATH:$SOAPUI/SoapUI-$SOAPUI_VERSION/bin"
COPY default-project.xml ${PROJECT_FOLDER}/
COPY entrypoint.sh /

ENTRYPOINT ["/entrypoint.sh"]
CMD ["start"]
