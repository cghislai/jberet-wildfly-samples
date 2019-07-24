# Overview

 This module contains sample web applications to demonstrate the use of JBeret
 and JSR 352 (Batch for Java Application) in WildFly and JBoss EAP. These sample
 apps use batch components in `jberet-support` to simplify accessing common data
 sources and formats.
 
 In all sample applications, the test client performs batch job tasks via REST API
 defined and implemented in `jberet-rest-api` module. 
 
 ```
 Test --> JAX-RS Client API = = = > WildFly/EAP --> jberet-rest-api --> Batch API & JBeret
 ```
 
## Sample Applications
* [restAPI](https://github.com/jberet/jberet-wildfly-samples/tree/master/restAPI)
    * tests and shows how to use JBeret REST API to access and manage batch job data.
* [restWriter](https://github.com/jberet/jberet-wildfly-samples/tree/master/restWriter)
    * uses `restItemWriter` to write batch data to destination resource via REST API.
    * uses `csvItemReader` to read data from online resource (movies-2012).
    * `restWriter` job inherits from reusable segments in parent JSL.
    * optionally include [jberet-ui](https://github.com/jberet/jsr352/tree/master/jberet-ui) in
    application package to provide a web front end for accessing batch job data.
* [restReader](https://github.com/jberet/jberet-wildfly-samples/tree/master/restReader)
    * uses `restItemReader` to read data from online resource (movies-2012).
    * uses `csvItemWriter` to write data to CSV format.
* [scheduleExecutor](https://github.com/jberet/jberet-wildfly-samples/tree/master/scheduleExecutor)
    * schedules single-action or recurring job executions using Java EE Concurrency Utils.
* [scheduleTimer](https://github.com/jberet/jberet-wildfly-samples/tree/master/scheduleTimer)
    * schedules single-action, recurring, or calendar-based job executions using Java EE Timer Service.
    * persistent or non-persistent job schedules.
* [batchProperty](https://github.com/jberet/jberet-wildfly-samples/tree/master/batchProperty)
    * demonstrates the injection of batch properties of common java types, such as `int`, `long`, `List`,
    `Date`, `BigInteger`, `Map`, `Set`, arrays, etc.
* [csv2json](https://github.com/jberet/jberet-wildfly-samples/tree/master/csv2json)
    * `csvItemReader` for reading data.
    * `jsonItemWriter` for writing data.
    * job inherits from parent JSL.
* [xml2json](https://github.com/jberet/jberet-wildfly-samples/tree/master/xml2json)
    * `xmlItemReader` for reading data.
    * `jsonItemWriter` for writing data.
    * job inherits from parent JSL.
* [xml2jsonLookup](https://github.com/jberet/jberet-wildfly-samples/tree/master/xml2jsonLookup)
    * same as `xml2json`, except that this sample looks up Jackson Json factory and XML factory in JNDI to
    improve resource efficiency.
* [csv2mongoLookup](https://github.com/jberet/jberet-wildfly-samples/tree/master/csv2mongoLookup)
    * `mongoItemWriter` for writing data.
    * `csvItemReader` for reading data.
    * looks up MongoDB client in JNDI to improve resource efficiency.
* [excelstream2csv](https://github.com/jberet/jberet-wildfly-samples/tree/master/excelstream2csv)
    * `excelEventItemReader` for reading data from Excel sheet.
    * `csvItemWriter` for writing data.
* [deserialization](https://github.com/jberet/jberet-wildfly-samples/tree/master/deserialization)
    * uses one custom class for checkpoint info, and another custom class for step persistent data, 
    to verify that they can be properly serialized and deserialized between job restart.
    * verifies the restartable job attribute.
    * verifies that a job whose job id differs from job xml file name can be started and restarted.
* [purgeJdbcRepository2](https://github.com/jberet/jberet-wildfly-samples/tree/master/purgeJdbcRepository2)
    * how to remove unwanted job data from a Jdbc job repository.
    * uses `org.jberet.repository.PurgeBatchlet`.
 
## Build, Deploy and Run
 
 A maven profile `wildfly` is defined to manage all WildFly-related tasks.
 In general, to clean and build the application, deploy it to WildFly or JBoss EAP, and 
 run all tests:
 
 ``` 
 mvn clean install -Pwildfly
 ```
 
To undeploy the application from WildFly or JBoss EAP:
 
 ``` 
 mvn clean -Pwildfly
 ```
 
 or
 
 ```
 mvn wildfly:undeploy
 ```
 
