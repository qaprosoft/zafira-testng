# Zafira::TestNG
## Integration
### Add Maven dependency
```
<dependency>
    <groupId>com.qaprosoft</groupId>
    <artifactId>zafira-client</artifactId>
    <version>${zafira-client.version}</version>
</dependency>
```

### Create [zafira.properties](https://github.com/qaprosoft/carina-demo/blob/master/src/main/resources/zafira.properties) and place to src/main/resources
```
zafira_enabled=true
zafira_service_url=http://localhost:8080/zafira-ws
zafira_access_token=
zafira_project=UNKNOWN
```

### Add ZafiraListener into your tests (use any option)
#### 1. Include using surefire plugin
```
<plugins>
    [...]
      <plugin>
        <groupId>org.apache.maven.plugins</groupId>
        <artifactId>maven-surefire-plugin</artifactId>
        <version>2.18.1</version>
        <configuration>
          <properties>
            <property>
              <name>listener</name>
              <value>com.qaprosoft.zafira.listener.ZafiraListener</value>
            </property>
          </properties>
        </configuration>
      </plugin>
    [...]
</plugins>
```
#### 2. Include using TestNG xml
```
<suite>
    [...]
      <listeners>
        <listener class-name="com.qaprosoft.zafira.listener.ZafiraListener"/>
      </listeners>
    [...]
</suite>
```
#### 3. Include @Listeners annotation
```
@Listeners({ZafiraListener.class})
public class LoginTest {
[...]
}
```

