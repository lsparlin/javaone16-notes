# Advanced Modular Development
Alan Bateman 
and Alex Buckley

## Application Migration
use `jdeps` to determine jar dependencies (in jdk 8)

```
module mylib {
	requires java.base;
	exports com.myapp.lib.util to myapp;
}

weak module myapp { // everything is exported (not as encapsulated)
	requires mylib;
	requires java.base;
	requires java.sql;
	requeres jackson.core;
	requires jackson.databind;
}
```

## Automatic modules
A jar file, that you put on the module path instead of the classpath

 * module name derived from the JAR file
 * exports ALL the packages
 * Requires ALL other modules

```
javac -- module-path lib -module-source-path src -d mods ...

jar --create --file mlib/mylib.jar -C mods/mylib .

jar --create --file mlib/myapp.jar -C mods/myapp . 
 --main-class myapp.Main

#  Run it
java --module-path mlib:lib -m myapp
```

## Migrating from the bottom
`jdeps --gen-module-info src *.jar`


