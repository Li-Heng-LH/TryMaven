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

##### Maven Plugins #####

* Maven is a framework that runs plugins. 
* A plugin can be thought of as a JAR file with exposed functionality. 
* There are three built-in life cycles: clean, default, site. 
* **Each life cycle consists of a sequence of phases**. clean: 3, default: 23, site: 4.
* Phases are executed in a specific order. 
* Running `mvn deploy` will not only execute _deploy_ phase, but all the phases before it as well, which is the entire 
_default_ lifecycle. 
* **Each phase is a sequence of goals**. When we run a phase, all goals bound to this phase are executed in order.
* **A plugin is a group of goals**. However, these goals are not necessarily all bound to the same phase.
* We can just run a specific goal, without executing its entire phase and the preceding phases. 

&nbsp;

* To build a project, `mvn deploy` executes the entire _default_ lifecycle.
* `mvn install` stops at the _install_ phase. 
* `mvn clean install` is usually used to clean the project first by running the clean lifecycle
* Can also run only a specific goal of the plugin: `mvn compiler:compile`.


&nbsp;

* CLEAN lifecycle removes files generated during build process. 
* By default removes /target directories. 
* Why we need clean? Refactoring and renaming classes -> old classes and artifacts are still there, causing unpredictable 
behaviour. 
* 

&nbsp;

#### Maven Commands ####

`mvn clean` cleans up build artifacts. E.g. the target directory. 



&nbsp;
&nbsp;

##### Credits #####
_Maven Goals and Phases_: https://www.baeldung.com/maven-goals-phases
