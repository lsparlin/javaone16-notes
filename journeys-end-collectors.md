# Journey's End - Streams and Collectors

### The life of a stream element

 * stream is born (spliterator)
 * transformed (by intermediate operations)
 * collected (by a terminal operation)

## Built-in Collectors

Other terminal operations
 * Search operations (`allMatch, anyMatch, findAny, findFirst`)
 * side-effecting operations (`forEach, forEachOrdered`)
 * reduce

### To define a collector, you need
 * Supplier
 * Accumulator
 * Combiner
 * [Finisher]

###  Predefined standalone collector
 * `toList(), toSet(), toMap(), joining()` 
 * `toCollection() (uses own supplier` - TreeMap, etc.)
 * `groupingBy(), partitioningBy(), groupingByConcurrent()` (classification map)

`people.stream().collect(Collectors.toSet());` (toSet is type `Collecor<Person, ?, Set<Person>>`)

### Custom Collection types
Can provide a supplier for type of map as the fourth parameter of `toMap`

`toCollection(Supplier<C> collectionFactory);`

### Classification maps

`groupingBy`
 * simple
 * with downstream collector
 * with downstream and map factory

#### Simple
```
...stream()
.collect(Collectors.groupingBy(Person::getCity));
// returns Map<City, List<Person>>
```

#### With Downstream Collector
```
....stream()
.collect(Collectors.groupingBy(Person::getCity, toSet()));
// returns Map<City, Set<Person>>
```
 
#### Map function before downstream collector
```
...stream()
.collect(Collections.groupingBy(person::getCity,
	mapping(Person::getName, joining()));
// returns Map<City, List<String>>
```

#### Convenience collecting methods
 `counting(), maxBy(), minBy(), summingXxx()`

#### Already threadsafe collections
 * `toConcurrentMap()`
 * `groupingByConcurrent()`

## Writing your own Collectors
Q: When do you want to do this?
A: Accumulate a container that doesn't implement `Collection`


