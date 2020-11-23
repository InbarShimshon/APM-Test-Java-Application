# APM-Test-Java-Application
The purpose of this repo is to provide a simple application containing an APM agent to easy set-up locally with the use of Springboot (SpingToolSuite4).

![image!](https://github.com/InbarShimshon/APM-Test-Java-Application/blob/main/image%20(4).png)



## What you need:
1) Some patience
2) Download the inbar-apm file
3) JDK 8 or later - https://www.oracle.com/java/technologies/javase-downloads.html
check version: `java -version`
4) Maven elastic-apm-agent https://search.maven.org/search?q=a:elastic-apm-agent
check version: `mvn -version`
5) Install Springboot https://docs.spring.io/spring-boot/docs/current/reference/html/getting-started.html

**Optional:** Spring Tool Suite (STS) - https://spring.io/guides/gs/sts/ (optional if you want to make changes to the code)

**Additional:** 
[Elastic-implementation]
(https://github.com/InbarShimshon/APM-Test-Java-Application/blob/main/Elastic-implementation) highlights the inbar-apm files modified in order to set up Elastic APM.





## Build executable .jar file (optional):
This is only relevant if you wish to make changes to the application and built a new executable .jar


*This will run Maven, telling it to execute the compile goal. When it’s finished, you should find the compiled .class files in the target/classes directory.*
```
mvn compile
```

*This will create an executable .jar file under target/classes directory*
```
~/path/to/inbar-apm/ mvn package
```


## Run application:

```
java -javaagent:/path/to/elastic-apm-agent-1.19.0.jar -Delastic.apm.service_name=my-apm-service -Delastic.apm.application_packages=inbar-apm -Delastic.apm.server_urls=http://localhost:8200 -jar path/to/inbar-apm/target/inbar-apm-0.0.1-SNAPSHOT.jar
```


## Test that it works:
1) In browser check localhost:8200 or cURL localhost:8200 a correct output looks like this:

```
{
  "build_date": "2020-11-09T18:39:24Z",
  "build_sha": "d5f4e01307540517d964edfe4af9d31227e0ce91",
  "version": "7.10.0"
}
```

You can now Launch APM in Kibana and see your agent listed.

2) You can test the application itself (unrelated to Elastic really but you can add/write your own code to push tests here)
In browser check localhost:8080 



