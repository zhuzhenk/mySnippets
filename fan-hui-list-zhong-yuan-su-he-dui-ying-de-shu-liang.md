```
public static <T> List<List<T>> pack(List<T> list) {
    T lastElement = null;
    List<List<T>> packedList = new ArrayList<>();
    List<T> elements = new ArrayList<>();
    for (T el : list) {
        if (!Objects.equals(lastElement, el)) {
            elements = new ArrayList<>();
            packedList.add(elements);
        }
        elements.add(el);
        lastElement = el;
    }
    return packedList;
}

P09.pack(list).stream().map(l -> new SimpleEntry<>(l.size(), l.get(0))).collect(toList());
//应该是可以写汉字的
```



