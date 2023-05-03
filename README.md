
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
