# Let's Get Lazy - Explore the Real Power of Streams
Venkat Subramaniam

## What does being lazy mean
 * Lazy Evaluation 
 * computation can be postponed

### Applicative Order vs Normal Order
Most languages use applicative order (like Java)

Normal order is when methods are called based on need

### Eager vs Lazy evaluation
Lazy eval only happens just before the result is needed

_awesome scala v java example_

Scala has `lazy val` syntax to force lazy evaluation when assigning variables

###  How do we do this in Java?
A: Lambda

```
Supplier<Integer> temp = () -> expensiveOp();
if (x > 5 && temp == 4) { ... }
```

### Laziness in Collections
A: Streams (fundamentally lazy)

```
List<Integer> values = Arrays.asList(1, 2, 3, 5, 4);

// find the double of the first even number of > 3
int result = 0;
for (int e : values) { // 8 computations
	if (e > 3 && e % 2 == 0) {
		result = e * 2;
		break;
	}
} 

// Functional solution
result = values.stream()
      .filter(e -> e > 3)
			.filter(e -> e % 2 == 0)
			.map(e -> 3 * 2)
			.findFirst() // Optional[8]
			.orElse(0);
```

### Can postpone things

```
public static int compute(int start, int count) {
	return Stream.iterate(start, e -> e + 1)
	             .filter(e -> e % 2 == 0)
							 .mapToInt(e -> e * 2)
							 .limit(count) // nothing has happend yet
							 .sum();
	return 0;
}

// print the total of double of 101 even numbers 
// starting with 51
System.out.println(compute(51, 101));

```

## Efficiency :)

http://agiledeveloper.com/downloads.html
