# JDK 9 Lang, Tooling, and Lib Features
Joseph Darcy @jddarcy

(start building JDK9 in CI)

## Info
 - Currenlty proposed for July 2017

## Read compatibility Guide

## How is 9 different?
 - More compatibility impact
 - Even breaking binary compatibility in some few cases
 - Deprecation policy

# Tooling

## jshell
 * `/help`
 * define variables
 * Lots of things

## JavaDoc
 * outputs HTML5
 * ` -html5`
 * search (new searc bar)

## cross compiling
 * `javac --release` - more concise than previous

## Multi-relase jar
 * in the META-INF/version directory

# Language Changes

## @SafeVarargs
	Basically gets rid of warnings for false positive vararg safety checks

 (can only be annotated on methods that cannot be overriden) 

## Diamond inferrance updates
 * Have to look at non-denotible types

## Private methods in interfaces

## New Deprecation annotation props
 * `@Deprecated(since="9", forRemoval=true)`

# Library Updates

## new version string scheme
`1.8` vs `9`

## JEP 254 Compact Strings
based on contents - either 1-byte or 2-byte characters

and optimized string concatenation

## Tiered Attribution
Fixes performance problem with nested <>

## Convenience Factory Methods
 * `Set<String> set = Set.of("a", "b", "c");` (YAY)
 * sets and maps
 


 Slides 
 https://blogs.oracle.com/darcy/resource/JavaOne/J1_2016_jdk9-lang-tools-libs.pdf
