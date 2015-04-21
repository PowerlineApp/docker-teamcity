FROM dockerfile/java:oracle-java8

RUN apt-get update && \
    apt-get install -y software-properties-common

RUN LANG=C.UTF-8 add-apt-repository ppa:ondrej/php5-5.6 && \
    apt-get update && \
    apt-get install -y php5-cli php5-fpm libzmq3-dev libzmq3 php5-dev php-pear pkg-config

RUN apt-get install -y nginx php5-common php5-curl php5-gd php5-mysql php5-sqlite php5-intl mysql-server curl ruby ruby-dev
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer --version=1.0.0-alpha10
RUN composer config -g github-oauth.github.com e10c7cdc7eb95d4e1f5d34a9e5cc809978c22013
RUN gem install fpm

RUN apt-get install software-properties-common && \
    apt-add-repository ppa:ansible/ansible && apt-get update && \
    apt-get install -y ansible

ADD setup-agent.sh /setup-agent.sh
RUN apt-get install -y unzip
RUN useradd -ms /bin/bash teamcity

EXPOSE 9090

CMD sudo -u teamcity -s -- sh -c "TEAMCITY_SERVER=$TEAMCITY_SERVER bash /setup-agent.sh run"
