# config-server-poc

This is poc of Centralized Config Server.

This project has two springboot applications

1. config-server (It act as config server)

******* Dependency to be added *******

	<dependency>
		<groupId>org.springframework.cloud</groupId>
		<artifactId>spring-cloud-config-server</artifactId>
	</dependency>
  
******* Annotation to be added in main method class *******

@EnableConfigServer

******* properties file(specify the github url where Configurations are present) *******

spring.application.name=config-server

spring.cloud.config.server.git.uri=https://github.com/Jaswanth-Stackroute/config-server.git
server.port=8888

2. Spring Boot application which connects to mongodb running in docker container(It act as config client)


 *******First run docker container of mongodb*******
 
 Command to run container --- 
               docker run -p 27017:27017 --name mongo -t mongo
 
******* Dependency to be added *******

<!-- https://mvnrepository.com/artifact/org.springframework.cloud/spring-cloud-starter-config -->
		<dependency>
			<groupId>org.springframework.cloud</groupId>
			<artifactId>spring-cloud-starter-config</artifactId>
			<version>2.1.4.RELEASE</version>
		</dependency>

******* properties file(specify the application name like demo-mongo if properties file name is demo-mongo.properties) *******

spring.application.name=demo-mongo
spring.cloud.config.uri=http://localhost:8888/

Now your spring boot application get configurations from demo-mongo.properties

In this case I specified url to connect to mongodb conatiner 

(spring.data.mongodb.uri=mongodb://0.0.0.0:27017/person)
