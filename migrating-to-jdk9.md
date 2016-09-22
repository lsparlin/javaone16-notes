# Migrating to JDK 9
Paul Bakker @pbakker

Sander Mak @Sander\_Mak 

_authors "Java 9 Modularity" http://shop.oreilly.com/product/0636920049494.do_

https://github.com/sandermak/java9-migration-demos

## Migrating modules onto the Classpath (temporary solution)
```
// Java 8
java -cp .. -jar myapp.jar

// Java 9
java -cp .. -jar myapp.jar # running as classpath still works

java -add-modules java.xml.bind -cp .. -jar myapp.jar # still running from the classpath
```

## 2 common errors
 * Unresolved platform modules
   * Classpath compile-time `java.se` module is used (not `java.se.ee`)
	 * `jdeps demo/Main.class` - will show unresolved dependencies
	 * `jdeps -internals ...` - even suggests replacements
 * (Ab)use of platform internals

## Introducing Modules (putting the classpath on the modules path)
Source path now contains module names between `src` and `main/test`
```
lib/
mods/
  ...jar
src/
  bookapp/
	  module-info.java
		main/
		test/
  books.api/
	books.impl/
	bookstore/
```

### Compile the module path
```
javac --module-source-path src -d out $(find . -name \'\*.java\')

java -mp out -m main/bookapp.BookApp;
```

## Migrating To Modules
_cannot reference the classpath from named modules!_

### Solution
 * A Plain JAR on the module path becomes an Automatic Module
 * Module name is derived from JAR name
 * Exports everything
 * Reads all other modules

### Migration Steps
 * Create monolithic module
 * Declare exports
 * figure out requires
 * move required jars to module path

## Tips
 1. Move libraries to the module path one by one (start with direct dependencies)
 2. `requires` only for direct dependencies (`--add-modules` for runtime/transitive dependencies)
 3. Create api modules and impl modules or have both in the same module and only export the API packages

## Recap
 * Try to run the application on the classpath using JDK 9
 * Create a module around your whole app
 * Finally: Modularize your application

