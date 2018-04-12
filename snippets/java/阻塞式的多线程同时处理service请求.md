```
@RunWith(SpringJUnit4ClassRunner.class)
@ContextConfiguration({"classpath:spring/ApplicationContext.xml"})
@ActiveProfiles("development")
public class ThreadPoolTest {
    @Autowired
    private CodeServiceAgent1 codeServiceAgent1;
    @Autowired
    private CodeServiceAgent2 codeServiceAgent2;
    @Autowired
    private CodeServiceAgent3 codeServiceAgent3;
    @Autowired
    private CodeServiceAgent4 codeServiceAgent4;
    @Autowired
    private CodeServiceAgent5 codeServiceAgent5;


//    @Test
    public void sync() {
        try {
            System.out.println("同步查询操作开始");
            LocalTime localTime = LocalTime.now();
            codeServiceAgent1.getCode("2");
            codeServiceAgent2.getCode("3");
            codeServiceAgent3.getCode("4");
            codeServiceAgent4.getCode("5");
            codeServiceAgent5.getCode("6");
            LocalTime localTime1 = LocalTime.now();
            System.out.println("用时" + localTime.until(localTime1, ChronoUnit.MILLIS));

        } catch (Exception e) {
            e.printStackTrace();
        }
    }

    @Test
    public void async() {
        try {
            System.out.println("异步查询操作开始");
            LocalTime localTime = LocalTime.now();
            ExecutorService executorService = new ThreadPoolExecutor(3, 5, 60,
                    TimeUnit.SECONDS,
                    new LinkedBlockingDeque<>(10),
                    new DefaultThreadFactory("service-pool", false),
                    new ThreadPoolExecutor.CallerRunsPolicy());
            Future<PageData> res1 = executorService.submit(new Callable<PageData>() {
                @Override
                public PageData call() throws Exception {
                    System.out.println(Thread.currentThread().getId()+"正在运行");
                    return codeServiceAgent1.getCode("2");
                }
            });
            Future<PageData> res2 = executorService.submit(() ->{
                System.out.println(Thread.currentThread().getId()+"正在运行");
                return codeServiceAgent2.getCode("3");
            } );
            Future<PageData> res3 = executorService.submit(new Callable<PageData>() {
                @Override
                public PageData call() throws Exception {
                    System.out.println(Thread.currentThread().getId()+"正在运行");
                    return codeServiceAgent3.getCode("4");
                }
            });
            Future<PageData> res4 = executorService.submit(new Callable<PageData>() {
                @Override
                public PageData call() throws Exception {
                    System.out.println(Thread.currentThread().getId()+"正在运行");
                    return codeServiceAgent4.getCode("5");
                }
            });
            Future<PageData> res5 = executorService.submit(new Callable<PageData>() {
                @Override
                public PageData call() throws Exception {
                    System.out.println(Thread.currentThread().getId()+"正在运行");
                    return codeServiceAgent5.getCode("6");
                }
            });
            System.out.println("这是阻塞式的，后面的语句得等计算完成后才能输出");
            PageData res1Pd= res1.get();
            System.out.println("第一个查询结束了");
            PageData res2Pd= res2.get();
            PageData res3Pd= res3.get();
            PageData res4Pd= res4.get();
            PageData res5Pd= res5.get();
            System.out.println("现在查询都完成了，阻塞结束");
            System.out.println(res1Pd.getString("code"));
            System.out.println(res2Pd.getString("code"));
            System.out.println(res3Pd.getString("code"));
            System.out.println(res4Pd.getString("code"));
            System.out.println(res5Pd.getString("code"));
            LocalTime localTime1 = LocalTime.now();
            System.out.println("用时" + localTime.until(localTime1, ChronoUnit.MILLIS));

        } catch (Exception e) {
            e.printStackTrace();
        }
    }


}
```



