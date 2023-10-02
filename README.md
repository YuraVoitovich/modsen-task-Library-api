# modsen-task-Library-api

# Booting 

You should run 
```code
  git clone "project path".
```
to clone all nessary mecroservices.

Then you should run maven instruction to build a .jar file for all related microservices:

```code
  mvn clean package
```

Then you should buid docker images for all microservices, running docker command: 


```code
  docker build -t "image name" "Dockerfile path"
```
You should use image names that are described in the docker-compose.yml, or use your names and change docker images names in the docker-compose.yml

Then you should run: 

```code
  docker-compose up
```


