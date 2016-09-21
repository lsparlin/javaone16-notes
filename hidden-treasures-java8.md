# A Few Hidden Treasures In Java 8
Venkat Subramaniam

## String Joining
```
import static java.util.stream.Collectors.*; 

List<String> names = Arrays.asList("Tom", "Jerry", "Jane");

// print the names in uppercase, comma separated
names.stream()
     .map(String::toUppercase)
		 .collect(joining(", ");
```

## Static Interface Methods
```
interface Util {
  public static int numberOfCores() {
    return Runtime.getRuntime().availableProcessors();
	}
}
```

## Default Methods
```
interface Fly {
  default void takeOff() { System.out.println("Fly::takeOff"); }
  default void turn()  { System.out.println("Fly::turn"); }
  default void cruise()  {System.out.println("Fly::cruise"); }
  default void land() { System.out.println("Fly::land"); }
}

interface FastFly implements Fly {
  default void takeOff() { System.out.println("FastFly::takeOff"); }
}

interface Vehicle {
  public void land() { System.out.println("Vehicle::land()"); }
}

interface Sail {
  default void cruise() { ... }
}

class SeaPlane extends Vehicle implemnts FastFly, Sail {

  public void cruise() { // MUST include an implementation if multiple interfaces have a default impl.
    FastFly.super.cruise();
	}
}
```

### 4 rules of default methods
 * You get what is in the base interface
 * You may override a default method (even in an implementing interface)
 * If a method is there in the class hierarchy then it takes precedence
 * If there is no method on any of the classes in the heirarchy, you must invoke rule 3

## Sorting and Grouping
```
import static java.util.stream.Collectors.*;
import static java.util.Comparator.comparing;

List<Person> people = Arrays.asList(
  new Person("Sarah", Gender.FEMALE, 20);
	...
);

// Collections.sort(people); // EVIL (mutates the list)

people.stream()
      .sort(comparing(Person::getAge).thenComparing(Person::getName).reversed()) // Comparator<Person> composed
			.forEach(System.out::println);


// group by age - just names
Map<Integer, String> ageToName = people.stream()
      .collect(groupingBy(Person::getAge, 
			 mapping(Person::getName, toList());
```

## Predicates and Functions
```
/* COMPOSING PREDICATES */
import  java.util.function.Precicate;

public static void print(int number, Predicate<Integer> predicate, String msg) {
	System.out.println(number + " " + msg + ":" + predicate.test(number));
}

Predicate<Integer> isEven = e -> e % 2 == 0;
Predicate<Integer> isGT4 = e -> e > 4;

print(5, isEven, "is even?");
print(10, isEven, "is even?");

print(5, isGT4, "is GT 4?");

// test both?
print(5, isGT4.and(isEven), "is > 4 && is even?");
```

## Maps convenient functions
```
public static double compute(int number) {
  System.out.println("called ..."):
	return Math.sqrt(number);
}

Map<Integer, Double> sqrt = new HashMap<>();

sqrt.computeIfAbsent(4, Sample::compute);
// computeIfPresent
```

## Parallelizing streams
```
public static int doubleIt(int number) {
  System.out.println(number + " : " + Thread.currenThread());
  return number * 2;
}

List<Integer> numbers = Arrays.asList(...);
numbers.parallelStream() 
       .map(Sample::doubleIt)
			 .reduce(0, Integer::sum);

// create your own ForkJoinPool to control number of threads 
```
