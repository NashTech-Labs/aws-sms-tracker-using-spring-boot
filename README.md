# aws-sms-tracker-using-spring-boot

An aws-sms-tracker to see the status of an SMS after the request Amazon Pinpoint is given. Similar to Tracker, SMS messages can have
states that Amazon can send us; such as SENT, RECEIVED. 

We can use Amazon Kinesis Data Streams to collect and process large streams of data records in real time. You can create
data-processing applications, known as Kinesis Data Streams applications. A typical Kinesis Data Streams application reads
data from a data stream as data records. These applications can use the Kinesis Client Library.


#### Technology

Java 8
Spring Boot 2.6.3 (with Spring Web MVC, Spring Data MongoDB)
MongoDB
Maven 3.6.1

#### Create & Setup Spring Boot project
Use Spring web tool or your development tool (Spring Tool Suite, Eclipse, Intellij) to create a Spring Boot project.

Then open pom.xml and add these dependencies:

<dependency>
	<groupId>org.springframework.boot</groupId>
	<artifactId>spring-boot-starter-web</artifactId>
</dependency>
<dependency>
    <groupId>com.amazonaws</groupId>
    <artifactId>aws-java-sdk-dynamodb</artifactId>
    <version>1.12.267</version>
</dependency>
<!-- https://mvnrepository.com/artifact/com.amazonaws/amazon-kinesis-client -->
<dependency>
    <groupId>com.amazonaws</groupId>
    <artifactId>amazon-kinesis-client</artifactId>
    <version>1.14.8</version>
</dependency>

#### Configure Spring Data MongoDB
Under src/main/resources folder, open application.yml and add following lines.

application:
name: aws-sms-tracker-demo
data:
mongodb:
uri: mongodb://${MONGO_HOST:localhost}:${MONGO_PORT:27017}/${spring.application.name}
profiles:
active: local

## Run Spring Boot application
mvn AwsSmsTrackerDemoApplication:run

Run the main application class and send the sms through the AWS Pinpoint services and check the status.

## References 
https://docs.aws.amazon.com/streams/latest/dev/shared-throughput-kcl-consumers.html

