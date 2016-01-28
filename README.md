# MapStream
MapStream is a convenient extension to the Java 8 Stream API that let you stream over Key-Value pairs. The project is a fork of the [Speedment MapStream component](http://github.com/speedment/speedment/) in case you want to use it as a stand-alone.

## Example Usage
```java
Map<String, Integer> numberOfCats = new HashMap<>();

numberOfCats.put("Anne", 3);
numberOfCats.put("Berty", 1);
numberOfCats.put("Cecilia", 1);
numberOfCats.put("Denny", 0);
numberOfCats.put("Erica", 0);
numberOfCats.put("Fiona", 2);

System.out.println(
  MapStream.of(numberOfCats)
      .filterValue(v -> v > 0)
      .sortedByValue(Integer::compareTo)
      .mapKey(k -> k + " has ")
      .mapValue(v -> v + (v == 1 ? " cat." : " cats."))
      .map((k, v) -> k + v)
      .collect(Collectors.joining("\n"))
);
```
Output:
```
Cecilia has 1 cat.
Berty has 1 cat.
Fiona has 2 cats.
Anne has 3 cats.
```

If you want to use static imports, replace `Collectors.joining("\n")` with `joining("\n")`.

## License
This code is available under the [Apache 2 license](http://www.apache.org/licenses/LICENSE-2.0). 
Attribution should be done to [Speedment, Inc.](http://speedment.org)
