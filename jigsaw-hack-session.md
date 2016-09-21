# Project Jigsaw Hack Session
## Q & A
Alan Bateman, Mark Renhold, Mandy Chung

> Read the JEPs 
http://openjdk.java.net/projects/jigsaw

### Q: Reflection
At runtime, if a class name is passed to a service like Jackson, does the class need to be 
in a exported package in order to be readable by Jacjson?
#### A: Yes, reflection follows the same encapsulation rules

### Q: A and B
If module A requires module B, can module B read module A?
#### A: No, that is a cyclic module graph

* jmods files are a new file type, mostly interally used by the JDK *


