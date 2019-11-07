FROM erlio/docker-vernemq


COPY ./vernemq_builder/vernemq.conf /vernemq/etc/vernemq.conf
COPY ./vernemq_log_plugin /vernemq/vernemq_log_plugin
USER root
#erlangを入れるときにjavaの依存関係のエラーが出るのでmkdir -p /usr/share/man/man1により回避
RUN apt-get update -y&&mkdir -p /usr/share/man/man1&&apt-get clean && apt-get install -y erlang git

WORKDIR /vernemq/vernemq_log_plugin/
RUN chmod 777 rebar3
RUN ./rebar3 compile
WORKDIR /vernemq/

USER vernemq
CMD ["start_vernemq"]

