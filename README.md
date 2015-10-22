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
      .mapValue(v -> v + " cats.")
      .collect(joining("\n"))
);
```
