# jenkins 
+ Jenkins is a self-contained, open source automation server which can be used to automate all sorts of tasks related to building, testing, and delivering or deploying software.

installations on 
+ we need to have java runtime in our os , 
To install java runtime 
```
sudo apt update
sudo apt install fontconfig openjdk-21-jre
java -version
```
T download and install jenkins 
> sudo wget -O /etc/apt/keyrings/jenkins-keyring.asc \
  https://pkg.jenkins.io/debian-stable/jenkins.io-2026.key
echo "deb [signed-by=/etc/apt/keyrings/jenkins-keyring.asc]" \
  https://pkg.jenkins.io/debian-stable binary/ | sudo tee \
  /etc/apt/sources.list.d/jenkins.list > /dev/null
sudo apt update
sudo apt install jenkins 

we can start jenkins 
+ `sudo systemctl enable jenkins`
+ `sudo systemctl start jenkins`
+ `sudo systemctl status jenkins`

Unlocking Jenkins
we can visit the jenkins on our localhost http://localhost:8080
+ `sudo cat /var/lib/jenkins/secrets/initialAdminPassword` we it to get the generated key to unload jenkins 
+ If you are running Jenkins in Docker using the official jenkins/jenkins image you can use sudo docker exec ${CONTAINER_ID or CONTAINER_NAME} cat /var/jenkins_home/secrets/initialAdminPassword to print the password in the console without having to open an interactive shell inside the container.
+ After we finish unlocking and installing plugins we need to create the first user account. 

we install docker and add jenkins to have access to docker 
```
sudo usermod -aG docker jenkins

sudo systemctl restart jenkins
```
after installing docker on our machine we install docker pipeline in jenkins so that jenkins can excute our pipelines in docker runtime.