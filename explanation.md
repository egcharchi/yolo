## This is the explanation file for the IP assignment
IP03 Requires us to make use of Ansible and Vagrant to be able to launch the application.  More Details after IP02 content below.
## Image Choices - Not more than 400mb, pushed to dockerhub
Chose the official node/alpine image as it was small, and the official mongo image for the db container
## Docker Directives
1.) Client
    FROM egcharchi/yolo-client:1.0.1
    WORKDIR /client
    COPY package.json .
    RUN npm install
    COPY . .
    EXPOSE 3000
    CMD ["npm", "start"]
2.) Backend
    FROM egcharchi/yolo-backend:1.0.1
    WORKDIR /backend
    COPY package.json .
    RUN npm install
    COPY . .
    EXPOSE 5000
    CMD ["npm", "start"]

3.) MongoDB
    database:
     image: egcharchi/yolo-mongodb:1.0.1
     container_name: yolo-mongodb
     ports:
      - "27017:27017"
     networks:
      - yolo-network
     volumes: 
      - ./data:/data/db
## Docker Compose Networking
The network was created in the docker-compose.yml
I gave it the name yolo-network and the type is bridge
## Docker Compose Volumes
I created a persistent volume called data/db in the mongodb container
## Git Workflow - Good Commits 10minimum
I did many local commits before pushing to github, each with a description of the main activity prior to saving, staging and committing.
## Application Deployment
#I am yet to successfully deploy on a cloud service provider, I am working on heroku.
The application is runninc containerized now.  
## Best Practices Followed - image tagging
Images were pulled, built and tagged using semver convention [repository]/[image]:[tag] in which the tag consists of [version.subversion.patch] eg. 1.0.1

## Running on Vagrant and Provisioning with Ansible - IP03
The containerized application was to be run on a vagrant VM and docker containers provisioned by ansible.

The vagrantfile:
Vagrant.configure("2") do |config|
   config.vm.box = "geerlingguy/ubuntu2004"
   config.vm.hostname = "yolovm"
   config.vm.provider "virtualbox" do |virtualbox|
      virtualbox.memory = "2048"
   end
   config.vm.network "private_network", ip: "192.168.56.53"
   config.vm.network "forwarded_port", guest: 3000, host: 3000
   config.vm.provision "ansible" do |ansible|
     ansible.verbose = "vv"
     ansible.playbook = "playbook.yml"
   end
 end
 
 I wanted the ansible feedback to be verbose so as to catch any issues easily.
