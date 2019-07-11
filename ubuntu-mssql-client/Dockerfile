FROM ubuntu:18.04

RUN apt-get update -y
RUN apt-get upgrade -y
RUN apt-get install -y libaio1 wget curl libssl1.0.0 libssl-dev gnupg gnupg2 gnupg1

RUN curl https://packages.microsoft.com/keys/microsoft.asc | apt-key add -
RUN curl https://packages.microsoft.com/config/ubuntu/18.04/prod.list > /etc/apt/sources.list.d/mssql-release.list

RUN apt-get update -y
RUN ACCEPT_EULA=Y apt-get install -y msodbcsql17
RUN apt-get install -y unixodbc unixodbc-dev
RUN ln -s  /etc/odbc.ini /usr/local/etc/odbc.ini
RUN ln -s /etc/odbcinst.ini /usr/local/etc/odbcinst.ini 
