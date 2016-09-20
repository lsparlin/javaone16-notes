# Java Libraries You Can't Afford to Miss
Andres Almiray @aalmiray
Ix-Chel Ruiz @ixchelruiz

http://github.com/aalmiray/javatrove

## Guice - for dependency Injection (JSR-330)

`Guice.createInjector(...) { @Override configure() { } }`

use `@Inject`

## SLF4J 

 * wraps other logging frameworks
 * provides varargs methods

## OkHttp
 * basic access to http and http2
 * configuration is extensible via factory classes
 * HTTP lifecycle can be decorated with interceptors

## Retrofit
 * wraps rest calls with Java interfaces
 * factories
 * has an extension for RxJava

## JDeferred - for promises
 * Promises can be chained
 * Java8 friendly
 * one shot execution

## RxJava - reactive programming
`Observable<?>` and `Subscription`

 * access to the observable pattern
 * delivers dozens of functional operations out of the box
 * Supports backpressure, when the data producer is faster than the consumer

## MBassador - an event bus
 * configurable event bux
 * Faster tha guava
 * No longer actively developed

## Lombok
 * builder pattern
 * annotations for boierplate
 * extensible - sorta
  
## JUnitParams
	
## Mockito - testing DSL and mocking
	* provides support for stubs, mocks, and spys
	* mock interfaces, abstract classes, and concrete classes

## Jukito
 * Guice integration with Mockito
 * allows injections and auto-mocks when no implementation

## Spock

## Awaitility
 * dsl for testing multi-threaded code
 * extensions for java8 
 * conditions can be customized
 
## Wiremock
