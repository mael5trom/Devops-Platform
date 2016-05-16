Requirements: 

1. You've added a node to Jenkins, and have the url availabile.
2. You're using authentication other than OAUTH and have a username and password for slave.
** Note, if you're using OAUTH and all users have logged into Jenkins and you've granted permissions, then disabling
will still allow those users to continue to log in ** 
3. Docker is installed
4. From this directory execute the following:
5. You have a file with needed configurations items, as shown below.

mkdir -p ../../../secrets && touch ../../../secrets/environment.txt

Add the following to environments.txt, modify with your settings.

JENKINS_URL=http://you_jenkins_server/computer/nodename
JENKINS_JOB_USERNAME=username
JENKINS_JOB_PASSWORD=password

Then: 

docker build -t jenkins-slave .
# To start interactively
docker run -i -t --env-file=../../../secrets/environment.txt jenkins-slave /bin/bash
# To start as daemon
docker run -d --env-file=../../../secrets/environment.txt jenkins-slave /bin/bash /jenkins/run.sh

** Note, this environment file is temporary and will be handled globally later **
