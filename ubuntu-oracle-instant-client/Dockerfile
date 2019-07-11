FROM ubuntu:latest

RUN apt-get update -y
RUN apt-get upgrade -y
RUN apt-get install -y alien libaio1 wget curl libssl1.0.0 libssl-dev

WORKDIR /tmp
RUN wget http://yum.oracle.com/repo/OracleLinux/OL7/oracle/instantclient/x86_64/getPackage/oracle-instantclient19.3-basic-19.3.0.0.0-1.x86_64.rpm
RUN wget http://yum.oracle.com/repo/OracleLinux/OL7/oracle/instantclient/x86_64/getPackage/oracle-instantclient19.3-devel-19.3.0.0.0-1.x86_64.rpm
RUN wget http://yum.oracle.com/repo/OracleLinux/OL7/oracle/instantclient/x86_64/getPackage/oracle-instantclient19.3-sqlplus-19.3.0.0.0-1.x86_64.rpm
RUN alien -i oracle-instantclient19.3-basic-19.3.0.0.0-1.x86_64.rpm
RUN alien -i oracle-instantclient19.3-sqlplus-19.3.0.0.0-1.x86_64.rpm
RUN alien -i oracle-instantclient19.3-devel-19.3.0.0.0-1.x86_64.rpm
RUN export LD_LIBRARY_PATH=/usr/lib/oracle/19.3/client64/lib/${LD_LIBRARY_PATH:+:$LD_LIBRARY_PATH}
RUN export ORACLE_HOME=/usr/lib/oracle/19.3/client64
RUN export PATH=$PATH:$ORACLE_HOME/bin
RUN ln -s /usr/include/oracle/19.3/client64 $ORACLE_HOME/include
RUN touch /etc/ld.so.conf.d/oracle.conf && chmod o+r /etc/ld.so.conf.d/oracle.conf
RUN echo '/usr/lib/oracle/12.2/client64/lib/' > /etc/ld.so.conf.d/oracle.conf
RUN ldconfig
RUN rm -f /tmp/*.rpm