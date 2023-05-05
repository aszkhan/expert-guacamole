
## How to setup locally

Java version: openjdk version "17.0.5" (Downloaded through Amazon Corretto). To install Java 17 use SDKMAN(Download SDKMAN through https://sdkman.io/install) and run command: 
```
>> sdk install java 17.0.5-amzn
```

Spring version: 2.7.10 with Gradle Groovy.

Steps after cloning the project:

1. Create database "elms-db".
2. Add line ```spring.profiles.active=dev``` when working locally. DO NOT PUSH THIS LINE OF CODE!
3. Build using the command: ./gradlew clean build.
4. Start the server after building the java project.
5. Open URL localhost:8080. If you receive the message "Up and running" the basic setup is done.

Steps to create and run docker image in local:-
1. Install docker.
2. Set profile to ```spring.profiles.active=local_docker``` in the application.properties file.
3. Build image: 
```
>> ./gradlew bootBuildImage --imageName=finflux/elms-platform
```
4. Establish docker network: 
```
docker network create finflux-elms-net
```
5. Create database: 
```
docker run --name elms-mysql-database -p3333:3306 --network finflux-elms-net -e MYSQL_ROOT_PASSWORD=mysql -e MYSQL_DATABASE=elms-db -d mysql
```
6. Run server locally in docker: 
```
docker run --network finflux-elms-net --name elms-platform-container -p 8090:8080 finflux/elms-platform
```
7. The server will run at ```http://localhost:8090```
