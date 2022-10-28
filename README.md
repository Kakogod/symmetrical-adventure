# symmetrical-adventure

# 1. Setup Jenkins on local machine and install a Java-Maven project.
* Make sure that the local machine has necesarry dependencies such as OpenJDK.
* Download Jenkins war package from https://www.jenkins.io/download/ .
* Initialize Jenkins with java -jar jenkins.war and wait for it to finish and boot up.
* Access Jenkins via Browser by using the default path localhost:8080.
* Install plugins, it is recommended that you pick "Install suggested plugins"
* Create admin user by filling out the necessary lines such as Username,Password , Full name and e-mail address.
* On Jenkins dashboard , press "New item" and create a new freestyle project with the name that you want.
* For my homework I used Spring petclinic example.
* Under Source Code Management I picked Git and pasted the following Repository URL https://github.com/g0t4/jgsu-spring-petclinic.git. 
* Under Branches to build I set branch specifier to "main.
* For Build Steps i picked execute shell and filled in the following command in order to build the package with Maven "./mvnw package"/
* Once finished , I booted up the build website with the command `java -Dserver.port=8081-jar target/spring-petclinic-2.3.1.BUILD-SNAPSHOT.jar` . I had to * specify a port as the default port (8080) was already in use to run Jenkins.

# 2.Setup Jenkins on AWS EC2 instance.
* After EC2 instance is booted up (t2 micro) I followed the next steps.
* Added the Jenkins repo: sudo wget -O /etc/yum.repos.d/jenkins.repo \
    https://pkg.jenkins.io/redhat-stable/jenkins.repo
* Imported a key file from Jenkins-CI to enable installation from the package: sudo rpm --import https://pkg.jenkins.io/redhat-stable/jenkins.io.key
* Performed a quick software update with : yup update -y
* Installed java dependencies before installing Jenkins: sudo amazon-linux-extras install java-openjdk11 -y
* Installed Jenkins: sudo yum install jenkins -y
* Enabled Jenkins with : sudo systemctl enable jenkins
* Boot up Jenkins with : sudo systemctl start jenkins
* From this point on you can follow the steps that were written on my first task.

# 3. Setup Lambda for stopping and starting EC2 instance (with Jenkins installed on).
I basically followed this good tutorial in order to setup Lambda. https://www.youtube.com/watch?v=mpaGMrzLJsA
