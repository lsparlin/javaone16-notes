# Prepare for JDK 9
Alan Bateman

 * Make Java Se more flexible
 * Improve seciryt and maintainability
 * Make it easier to construct, maintain, deploy large applications
 * Enable improved performance

## Background: Categories of API's in JDK
 * Supported
   * JCP standar, java., javax.
	 * JDK-specific API com.sun.
 * Unsupported JDK-internal, not intended for external use sun.

> If an application uses only supported APIs and works on release N, then it should work on N+1, even without recompilation

> Supported apis can be removed, but with advanced notice

## Incompatible changes in JDK 9
 * non-critical internal api's will be encapsulated JEP 260
 * Cange the binary structure of the JRE and JDK JEP 220
   * JRE and JDK separation will no longer exist
 * Removed some deprecated methods (JSR 337 and JEP 162)
 * modules shared with Java EE are not resolved by default JEP 261 (modularization does not allow split packages between modules and classpath)
 * Bootclasspath has been removed (and system property sun.boot.class.path)
 * New version-string scheme JEP 223 (1.9 -> 9) - also new Version api

## JDEPS tool introduced in JDK 8 - helps find internal API uses
`jdeps -jdkinternals [jar file]` shows jars depended upon

_Theres a maven plugin too_

`--add-exports` command line option can include encapsulated libraries from a module in the runtime

## New features to help with migration

 * multi-release JAR `META-INF/versions/[version-number]/`


