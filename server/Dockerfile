FROM dockerfile/java:oracle-java8

ENV TEAMCITY_DATA_PATH /data/teamcity
ENV TEAMCITY_PACKAGE ./TeamCity-2017.2.2.tar.gz

ADD $TEAMCITY_PACKAGE /opt

EXPOSE 8111
CMD ["/opt/TeamCity/bin/teamcity-server.sh", "run"]

