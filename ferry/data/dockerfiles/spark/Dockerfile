FROM $USER/gluster
NAME spark

# Make the various directories needed
RUN mkdir -p /service/packages /service/data/main /service/data/logs /service/data/tmp /service/data/staging /service/sbin /service/scripts

# Download some dependencies
RUN apt-get --yes install openjdk-7-jdk zlib1g lib32z1 software-properties-common
RUN wget http://d3kbcqa49mib13.cloudfront.net/spark-0.9.0-incubating-bin-hadoop2.tgz -P /service/packages;cd /service/packages;tar -xzf spark-0.9.0-incubating-bin-hadoop2.tgz

# untar tarball and  move the untarred files to /hadoop
RUN ln -s /service/packages/spark-0.9.0-incubating-bin-hadoop2/conf /service/conf;ln -s /service/packages/spark-0.9.0-incubating-bin-hadoop2 /service/packages/spark

# Soft links to make life easier
RUN ln -s /service/packages/spark/bin/* /usr/local/bin/
RUN ln -s /service/packages/spark/sbin/* /usr/local/sbin/

# Make ferry owner of everything. 
RUN chown -R ferry:docker /service

ENV JAVA_HOME /usr/lib/jvm/java-7-openjdk-amd64
RUN echo export JAVA_HOME=/usr/lib/jvm/java-7-openjdk-amd64 >> /etc/profile
