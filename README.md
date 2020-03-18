## spring全家桶系列
### 03 leo-spring-multiple-datasource
本例子使用多个h2 数据源做演示

**知识点一**

关于如下代码的解释：
```java
@SpringBootApplication(exclude = {DataSourceAutoConfiguration.class,
        DataSourceTransactionManagerAutoConfiguration.class,
        JdbcTemplateAutoConfiguration.class})
```
这是禁止springboot自动加载数据源，因为 @EnableAutoConfiguration 注解，我们在引入
spring-boot-starter-data-jdbc、Mongdb等jar时，里边会自动为我们配置数据源，但是我们的程序中又通过
@Configuration 注解配置了数据源，就会导致在加载一次，前后就会冲突，所以要排查springboot为我们自动加载的数据源

**知识点二**
连接池HikariCP的使用可以参考文件：
org.springframework.boot.autoconfigure.jdbc.DataSourceConfiguration

