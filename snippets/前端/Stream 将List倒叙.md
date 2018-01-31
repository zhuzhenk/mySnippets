```
int size = list.size();
List list = IntStream.iterate(size - 1, el -> el - 1).limit(size).mapToObj(list::get).collect(toList());
```



