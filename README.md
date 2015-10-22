# MapStream
A fork of the Speedment MapStream component if you want to use it as a stand-alone.

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
      .mapKey(k -> k + " has ")
      .sortedByValue(Integer::compareTo)
      .mapValue(v -> v + (v == 1 ? " cat." : " cats."))
      .collect(joining("\n"))
);
```
Output:
```
Berty has 1 cat.
Cecilia has 1 cat.
Fiona has 2 cats.
Anne" has 3 cats.
```
