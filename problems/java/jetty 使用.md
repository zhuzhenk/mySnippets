```
jetty:run -Djetty.http.port=8080
或者jetty:run

 <plugin>
    <groupId>org.mortbay.jetty</groupId>
    <artifactId>jetty-maven-plugin</artifactId>
    <version>8.1.16.v20140903</version>
    <configuration>
        <stopPort>9988</stopPort>
        <stopKey>foo</stopKey>
        <scanIntervalSeconds>5</scanIntervalSeconds>
        <connectors>
            <connector implementation="org.eclipse.jetty.server.nio.SelectChannelConnector">
                <port>8080</port>
                <maxIdleTime>60000</maxIdleTime>
            </connector>
        </connectors>
        <webAppConfig>
            <contextPath>/</contextPath>
        </webAppConfig>
    </configuration>
</plugin>


这个jetty在maven窗口中不会自动出现很奇怪，需要自己写个maven启动
```



