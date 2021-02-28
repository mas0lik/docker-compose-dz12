#Stagin environmet is created using base Ubuntu 20.04 image
FROM ubuntu:20.04

#Update and install tools required to build app
RUN apt-get update
RUN apt-get install default-jdk -y
RUN apt-get install git -y
RUN apt-get install maven -y

#Clone git repo and set context
WORKDIR /home/pkhramchenkov/
RUN git clone https://github.com/shephertz/App42PaaS-Java-MySQL-Sample.git
WORKDIR /home/pkhramchenkov/App42PaaS-Java-MySQL-Sample/

#Replace content of 'Config.properties' with actual database parametres for app-db connection prior build
RUN /bin/bash echo -e "app42.paas.db.username = paasdb_user" > WebContent/Config.properties
RUN /bin/bash echo -e "app42.paas.db.port = 3306" >> WebContent/Config.properties
RUN /bin/bash echo -e "app42.paas.db.password = secret" >> WebContent/Config.properties
RUN /bin/bash echo -e "app42.paas.db.ip = mysql" >> WebContent/Config.properties
RUN /bin/bash echo -e "app42.paas.db.name = paasdb" >> WebContent/Config.properties

#Build app
RUN mvn package