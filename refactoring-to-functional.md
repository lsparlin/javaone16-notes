# Refactoring to Functional Style using Java 8
Venkat Subramaniam @venkat_s

http:/www.agiledeveloper.com

## Functional Style
 * higher order functions
 * immutability
 * declarative style
 * lazy evaluation

## Imperitive vs functional: is prime
 * Familiar vs simple
 * imperitive impl is noisy
 * no garbage variables

```
// Imperitive
public static boolean isPrime(int nmber) {
	for() {
		if {
			...
		}
	}
	return number?;
}
```
```
// Functional solution
public static boolean isPrime(int number) {
  return number> 1 && IntStream.range(2, number)
    .noneMatch(i -> number % i == 0);
}
```

## Imperitive vs functional: Line count
 * no explicit mutability
 * using stream and filter

Imperitive impl is too much to type 

```
// Functional solution
import java.nio.file.*;

// Files.lines returns stream()
long count = Files.lines(Paths.get(path))
  .filter(line -> line.contains(searchWord))
	.count();`
```

## Imperitive vs functional: grouping by score
 * from verbose to concise
 * highly expressive
 * declarative

Imperitive style is quite familar - create map, loop through everything, checking for existance, getting list, adding to list

```
// Functional solution
static import java.util.stream.Collectors.groupingBy;
return scores.keySet()
  .stream()
	.collect(groupingBy(scores::get));
```

## Imperitive vs functional: decorator
 * bloated OO to 

```
// Functional solution

Predicate<Applicant> xxxEvaluator = Applicant::isCredible;

Predicate.and()
```

## pythagorean tripleG
