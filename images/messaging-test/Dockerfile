FROM manageiq/ruby:latest

ENV BUNDLE_GEMFILE=/opt/messaging-test/Gemfile

RUN yum install -y git nmap-ncat which
RUN gem install bundler

COPY app /opt/messaging-test
COPY entrypoint /usr/bin
RUN cd /opt/messaging-test && bundle install

ENTRYPOINT [ "entrypoint" ]
