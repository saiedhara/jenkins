# jenkins
practice jenkins by short scripts


#Install Jenkins on AWS EC2

Prerequisites:-

EC2 RHEL
With Internet Access
Security Group with Port 8080 open for internet
Java v1.8.x

#Install Java

yum install java-1.8*
#yum -y install java-1.8.0-openjdk



confirm the Java Version
Lets install java and set the java home

java -version
find /usr/lib/jvm/java-1.8* | head -n 3
#JAVA_HOME=/usr/lib/jvm/java-1.8.0-openjdk-1.8.0.191.b12-1.el7_6.x86_64
export JAVA_HOME
PATH=$PATH:$JAVA_HOME
# To set it permanently update your .bash_profile
source ~/.bash_profile

[root@~]# java -version

Install Jenkins
You can install jenkins using the rpm or by setting up the repo. We will setup the repo so that we can update it easily in future. Get latest version of jenkins from https://pkg.jenkins.io/redhat-stable/

yum -y install wget
wget -O /etc/yum.repos.d/jenkins.repo https://pkg.jenkins.io/redhat-stable/jenkins.repo
rpm --import https://pkg.jenkins.io/redhat-stable/jenkins.io.key
yum -y install jenkins
Start Jenkins
# Start jenkins service
systemctl start jenkins

# Setup Jenkins to start.
systemctl enable jenkins


Accessing Jenkins
By default jenkins runs at port 8080, You can access jenkins at

http://YOUR-SERVER-PUBLIC-IP:8080
Configure Jenkins
The default Username is admin
Grab the default password
Password Location:/var/lib/jenkins/secrets/initialAdminPassword
Skip Plugin Installation; We can do it later
Change admin password
Admin > Configure > Password
Configure java path
Manage Jenkins > Global Tool Configuration > JDK
Create another admin user id
