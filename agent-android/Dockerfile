FROM ahazem/android:v0.7.6

RUN apt-get install -y sudo unzip software-properties-common
RUN add-apt-repository ppa:chris-lea/node.js && apt-get update
RUN apt-get install -y nodejs
RUN npm install -g bower grunt-cli

ADD setup-agent.sh /setup-agent.sh

RUN useradd -ms /bin/bash teamcity

EXPOSE 9090

CMD sudo -u teamcity -s -- sh -c "TEAMCITY_SERVER=$TEAMCITY_SERVER bash /setup-agent.sh run"
