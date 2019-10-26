### Some Learning Notes ###

&nbsp;

#### Creating Java jar files from Command Line ####

In the BeforeMaven folder, to package HelloWorld.class, run: 

`jar cf HelloWorld.jar HelloWorld.class`

where cf stands for "create file". 

To execute the class file in the jar, run: 

`java -classpath HelloWorld.jar HelloWorld`

&nbsp;

#### Using 3rd Party Jars with Command Line Java ####

To compile the java file which utilises a 3rd party library, 
run: 

`javac -classpath ./lib/* HelloWorld.java`

`./lib/*` tells compiler to include everything in the lib folder. Without it, compiler will not be able to compile.  

To run the new class file that utilises the 3rd party library, run:

`java -classpath ./lib/*:./ HelloWorld`

`./lib/*:./` picks up everything in the lib, as well as the root folder. Without it, JVM will not be able to run. 

&nbsp;

#### Maven Concepts ####

##### Maven Coordinates #####

* Maven **artifacts** are in **target** directory.
* Maven **Coordinates**: **groupId**, **artifactId**, **version**. Together, they identify a location in the maven repository. 
* Version number: major.minor.incremental
* Snapshot: SNAPSHOT suffix is an important maven qualifier. It tells maven that this is a development version 
and it is not stable. 
* Without SNAPSHOT suffix, maven will download the artifact into local repository and will never check in the remote 
repository again. 
* With SNAPSHOT suffix, maven will check for newer versions.

##### Maven Repositories #####
* Local, Central, Remote
* Central: http://repo1.maven.org/ or https://mvnrepository.com/

##### Maven POM #####
* Effective POM: POM that is complete with inherited properties. 

##### Maven Dependencies #####
* Cyclic dependencies are not supported. 
* Dependency Mediation: A->B, A->D2.0, B->D1.5. D2.0 will be included. 
* Dependency Scope: If JUnit and Mockito are not declared in test scope, that is like telling people downstream that they
need JUnit and Mockito. This will cause people pain in the down road in open source projects. 
* 


&nbsp;

#### Maven Commands ####

`mvn clean` cleans up build artifacts. E.g. the target directory. 



