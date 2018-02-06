```
<dependency>
    <groupId>org.hashids</groupId>
    <artifactId>hashids</artifactId>
    <version>1.0.3</version>
</dependency>
 
 Hashids hashids  = new Hashids("123456789qwer");
 long[] origin = {123123123, 2, 0, 1, 7, 0, 9};
 String  a = hashids.encode(origin).toString();
 System.out.println(a);
 Arrays.stream(hashids.decode(a)).forEach(value ->System.out.println(value) );
```



