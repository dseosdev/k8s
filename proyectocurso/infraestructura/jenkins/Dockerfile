FROM jenkins/jenkins

USER root

RUN apt-get update && apt-get install -y \
    apt-transport-https \
    software-properties-common \
    sudo

RUN curl -fsSL https://download.docker.com/linux/ubuntu/gpg | apt-key add -
RUN add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu xenial stable"

RUN apt-get update && apt-get install -y \
    docker-ce

RUN usermod -aG docker,staff jenkins


RUN echo "jenkins ALL=NOPASSWD: ALL" >> /etc/sudoers

# install kubectl
RUN curl -LO https://storage.googleapis.com/kubernetes-release/release/$(curl -s https://storage.googleapis.com/kubernetes-release/release/stable.txt)/bin/linux/amd64/kubectl; chmod +x ./kubectl; mv ./kubectl /usr/local/bin/kubectl

 
#USER jenkins

ENTRYPOINT ["/usr/local/bin/jenkins.sh"]