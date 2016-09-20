# Project Jigsaw: Under the Hood
Alex Buckley

## JDK 9 at a glance
 * Module System
 * Modular JDK
 * Language Enhancements
 * Library enhancements
 * Tool enhancements

## Accessibility and Readability
Accessibility heirarchy has always been clear, but maybe too generous
 * public
   * public to everyone
	 * public but only to specific modules
	 * public only within a module
 * protected
 * <package>
 * private

_pre JDK 9 public is available to EVERYONE_

> public no longer means "accessible"

### Class loaders
 * Traditionally class loaders have been used to encapsulate packages, but this is not strong encapsulation
 * Strong encapsulation means even in the same loader, a un-exported package is unaccessible (even with reflection)
 * Accessibility is independent of class loaders (only modules)

### Strong encapsulation means reflection will not access private properties or public properties of non-public types
can be changed by developer with `exports private package`

### Think transitively about dependencies
use `requires transitive java.logging` to say that other dependencies also need to require java.logging

## Named Modules
 * everything on the classpath is one big module
  * they read every named module
	* named modules do not read unnamed modules (classpath) out of the box
 * moving a jar to the module path creates an automatic module which reads all other modules
  * it also reads the unnamed modules	
	* auto modules export all their packages
 
### Loaders and Layers
The model of class loading in JDK 9 is unchanged

*Bootstrap Loader <- Platform Loader <- Application Loader*

### Where is the module system
The module system is inside the Application Loader

## The Road Ahead

