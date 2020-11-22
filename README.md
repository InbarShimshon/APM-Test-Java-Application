# APM-Test-Java-Application
The purpose of this repo is to provide a simple application containing an APM agent to easy set-up locally with the use of Springboot (SpingTookSuite4).



## What you need:

1) Some patience
2) Download the inbar-apm file
3) JDK 8 or later - https://www.oracle.com/java/technologies/javase-downloads.html
check version: `java -version`
4) Maven elastoc-apm-agent https://search.maven.org/search?q=a:elastic-apm-agent
check version: `mvn -version`
5) Install Springboot https://docs.spring.io/spring-boot/docs/current/reference/html/getting-started.html

*Optional:* Spring Tool Suite (STS) - https://spring.io/guides/gs/sts/ (optional if you want to make changes to the code)

What does the inbar-apm file contain for Elatsic APM:

in pom.xml

```
<?xml version="1.0" encoding="UTF-8"?>
<project xmlns="http://maven.apache.org/POM/4.0.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
	xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 https://maven.apache.org/xsd/maven-4.0.0.xsd">
	<modelVersion>4.0.0</modelVersion>
	<parent>
		<groupId>org.springframework.boot</groupId>
		<artifactId>spring-boot-starter-parent</artifactId>
		<version>2.4.0</version>
		<relativePath/> <!-- lookup parent from repository -->
	</parent>
	<groupId>com.example</groupId>
	<artifactId>inbar-apm</artifactId>
	<version>0.0.1-SNAPSHOT</version>
	<name>inbar-apm</name>
	<description>Demo APM</description>

	<properties>
		<java.version>11</java.version>
	</properties>

	<dependencies>
		<dependency>
			<groupId>org.springframework.boot</groupId>
			<artifactId>spring-boot-starter</artifactId>
		</dependency>
		<dependency>
			<groupId>org.springframework.session</groupId>
			<artifactId>spring-session-core</artifactId>
		</dependency>
		

		<dependency>
			<groupId>org.springframework.boot</groupId>
			<artifactId>spring-boot-starter-test</artifactId>
			<scope>test</scope>
		</dependency>
		
		<dependency>
            <groupId>org.springframework.boot</groupId>
             <artifactId>spring-boot-starter-web</artifactId>
         </dependency>
		
		
	</dependencies>

	<build>
		<plugins>
			<plugin>
				<groupId>org.springframework.boot</groupId>
				<artifactId>spring-boot-maven-plugin</artifactId>
			</plugin>
		</plugins>
	</build>

</project>



```

application.properties

```
service_name=apmapp
server_urls=https://xxxxxxxxxxxx.apm.europe-west4.gcp.elastic-cloud.com:443
secret_token=sygKs0LGyBIHzCxMwq
application_packages=inbar-apm
server.error.whitelabel.enabled=false

```





## Build executable .jar file:

```
mvn compile

```
This will run Maven, telling it to execute the compile goal. When it’s finished, you should find the compiled .class files in the target/classes directory.

```
~/inbar-apm inbarshimshon% mvn package
```
this will create an executable .jar file under target/classes directory


## Run application:
```

java -javaagent:/path/to/elastic-apm-agent-1.19.0.jar -Delastic.apm.service_name=my-apm-service -Delastic.apm.application_packages=inbar-apm -Delastic.apm.server_urls=http://localhost:8200 -jar path/to/inbar-apm/target/inbar-apm-0.0.1-SNAPSHOT.jar
```
