```
public static final String CLASSPATH = new File(AttachController.class.getResource("/").getPath()).getPath() + File.separatorChar;
boolean existInstall = Files.exists(Paths.get(AttachController.CLASSPATH + "install.lock"));

System.getProperty("user.dir")
//也是获取项目根路径
```



