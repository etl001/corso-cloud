FROM jenkins/jenkins:2.290-jdk11
USER root
RUN apt-get update && \
    apt-get install -y maven \
                       gnupg2 \
                       software-properties-common curl \
                       pass  \
                       docker  \
                       docker-compose && \
    curl -fsSL https://apt.releases.hashicorp.com/gpg | apt-key add - && \
    apt-add-repository "deb [arch=amd64] https://apt.releases.hashicorp.com $(lsb_release -cs) main" && \
    apt-get update && \
    apt-get -y install terraform && \
    curl https://raw.githubusercontent.com/helm/helm/master/scripts/get-helm-3 | bash && \
    curl -LO "https://dl.k8s.io/release/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl" && \
    install -o root -g root -m 0755 kubectl /usr/local/bin/kubectl && \
    apt-get install -y software-properties-common && \
    echo "deb http://ppa.launchpad.net/ansible/ansible/ubuntu trusty main" >> /etc/apt/sources.list && \
    apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 93C4A3FD7BB9C367 && \
    apt-get update && \
    apt-get -y install ansible && \
    apt-get install make && \
    apt-get clean && \
    curl -sL https://aka.ms/InstallAzureCLIDeb | bash && \
    usermod -aG docker jenkins && \
    touch /var/run/docker.sock && \
    chown :docker /var/run/docker.sock