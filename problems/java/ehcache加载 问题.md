```
Failed to load class org.slf4j.impl.StaticLoggerBinder
This warning message is reported when the org.slf4j.impl.StaticLoggerBinder class could not be loaded into memory.
 This happens when no appropriate SLF4J binding could be found on the class path. Placing one (and only one) 
 of slf4j-nop.jar slf4j-simple.jar, slf4j-log4j12.jar, slf4j-jdk14.jar or logback-classic.jar on the class
  path should solve the problem.

  slf4j 找不到具体实现类了，加入其中一个jar即可，但是要是编译级别的
  
  还有 记住@Cacheable
  @CacheEvict
  @CachePut
  这三个注解
  
  还有一个问题就是在测试service的时候，
  @SpringBootTest(classes = Log4j2DemoApplication.class, webEnvironment = SpringBootTest.WebEnvironment.MOCK)
  这个classes 指代的是springboot的启动类，开始写成了要测试的类，导致报错
  
```



