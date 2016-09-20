# Introduction to Modular Development
Alan Bateman 

## Modular development starts with A Modular Platform

 * `java --list-modules [module-name]`
 * Java Linker - links a set of modules and creates a runtime image
 * `jlink --module-path jomods/ --add-modules java.desktop --output myimage`
 * `myimage/bin/java --list-modules`
 
## Intro to Modules

 * module-info.java
 * `module stats.core {}`
 * "java.sql reads java.core" - means java.sql depends on java.core
 * `requires transitive` - any dependnecy of this modules will also read this module
 * `exports package-name`
 * *public no longer implies accessibility* outside the module

` java -p modpath -m module.name/com.things.MainClass `

` -Xdiag:resolver` - more details about module resolving

### Modular Jar
Regular Jar file, but has a module-info.class inthe top directory

`jar ... --print-module-descriptor`

Can now run java with just a module name
`java -p mlib -m module.name`

## Modules and libraries can be mixed
`java -p mlib --add-modules mod.name -jar stats-gui.jar`

`jlink --module-path $JDKMODS:mlib:mlib2 --add-modules other.mod --output myimage`
