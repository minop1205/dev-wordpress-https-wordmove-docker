FROM ruby:2.5

RUN apt update && \
    apt install -y bash mysql-client rsync apt-file apt-transport-https lsb-release ca-certificates && \
    wget -O /etc/apt/trusted.gpg.d/php.gpg https://packages.sury.org/php/apt.gpg && \
    echo "deb https://packages.sury.org/php/ $(lsb_release -sc) main" > /etc/apt/sources.list.d/php.list && \
    apt-file update && \
    apt install -y php5.6 && \
    gem install wordmove && \
    mkdir ~/.ssh

COPY settings/movefile.yml /home/movefile.yml
COPY ssh-keys/id_rsa /root/.ssh/id_rsa
COPY settings/default.rb /usr/local/bundle/gems/wordmove-3.0.2/lib/wordmove/sql_adapter/default.rb

RUN chmod 700 /root/.ssh/id_rsa
