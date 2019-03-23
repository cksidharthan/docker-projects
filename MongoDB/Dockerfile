FROM centos

# Add mongo Repo
RUN echo -e "\
[mongodb]\n\
name=MongoDB Repository\n\
baseurl=https://repo.mongodb.org/yum/redhat/7Server/mongodb-org/3.2/x86_64/\n\
gpgcheck=0\n\
enabled=1\n\
gpgkey=https://www.mongodb.org/static/pgp/server-3.2.asc" >> /etc/yum.repos.d/mongodb.repo

# Install and Configure MongoDB
RUN yum update -y && \
    yum install mongodb-org -y && \
    mkdir -p /data/db && \
    echo "security:" >> /etc/mongod.conf && \
    echo "  authorization: enabled" >> /etc/mongod.conf

EXPOSE 27017
ENTRYPOINT ["/usr/bin/mongod --fork --logpath /var/log/mongodb.log"]
