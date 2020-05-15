Installation


See https://github.com/jenkinsci/docker/blob/master/README.md

Open some ports on the firewall

Create the project directory
```
mkdir -p ~/dev/docker/projects/jenkins;
```

Add the hostname in the /etc/hosts file
```
127.0.1.1 dev.jenkins
```

Create a docker-secrets.sh file and run it
```
cd ~/dev/docker/projects/jenkins;
vi docker-secrets.sh
chmod +x docker-secrets.sh
./docker-secrets.sh
```

Copy the some files
```
scp ~/dev/docker/projects/jenkins/docker-compose.yml stephane@thalasoft.com:~/dev/docker/projects/jenkins
```

Create the volume directories
```
mkdir -p ~/dev/docker/projects/common/volumes/jenkins;
```

Create some log files
```
touch ~/dev/docker/projects/common/volumes/logs/jenkins.log;
```

Pull the images
```  
docker pull thalasoft.com:5000/fail2ban;
```

Read and follow all the INSTALLATION.md files of the project

Access the server
```  
http://dev.jenkins:8082
```  

Viewing the generated secret
```  
cat ~/dev/docker/projects/common/volumes/jenkins/secrets/initialAdminPassword
```  

Start the services
```  
cd ~/dev/docker/projects/jenkins
docker stack deploy --compose-file docker-compose.yml jenkins
```

Stopping the common services
```  
docker stack rm jenkins
```

