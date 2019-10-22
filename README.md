### Some Learning Notes ###

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



