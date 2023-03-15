## This is the explanation file for the IP assignment

## Image Choices - Not more than 400mb, pushed to dockerhub
Chose the official node/alpine image as it was small, and the official mongo image for the db container
## Docker Directives
1.) Client
    FROM egcharchi/yolo-client:1.0.0
    WORKDIR /client
    COPY package.json package.json
    RUN npm install
    COPY . .
    EXPOSE 5000
    CMD ["npm", "run", "start"]
2.) Backend
    FROM egcharchi/yolo-backend:1.0.0
    WORKDIR /backend
    COPY package.json package.json
    RUN npm install
    COPY . /backend
    EXPOSE 5000
    CMD [ "npm", "run", "start" ]
3.) MongoDB
    database:
     image: egcharchi/yolo-mongodb:1.0.0
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
I am yet to successfully deploy on a cloud service provider, I am working on heroku.
## Best Practices Followed - image tagging
Images were pulled, built and tagged using semver convention [repository]/[image]:[tag] in which the tag consists of [version.subversion.patch] eg. 1.0.0