# Error Vault
This document contains collection of errors with their resolution.

#### 0.0.1-Error
```Error creating bean with name 'dataSourceScriptDatabaseInitializer' defined in class path resource [org/springframework/boot/autoconfigure/sql/init/DataSourceInitializationConfiguration.class]: Unsatisfied dependency expressed through method 'dataSourceScriptDatabaseInitializer' parameter 0: Error creating bean with name 'dataSource' defined in class path resource [org/springframework/boot/autoconfigure/jdbc/DataSourceConfiguration$Hikari.class]: Failed to instantiate [com.zaxxer.hikari.HikariDataSource]: Factory method 'dataSource' threw exception with message: Cannot load driver class: com.mysql.jdbc.Driver```

```Error creating bean with name 'entityManagerFactory' defined in class path resource [org/springframework/boot/autoconfigure/orm/jpa/HibernateJpaConfiguration.class]: Unable to create requested service [org.hibernate.engine.jdbc.env.spi.JdbcEnvironment] due to: Unable to resolve name [org.hibernate.dialect.MySQL5Dialect] as strategy [org.hibernate.dialect.Dialect]```
#### Resolution
```xml
<dependency>
    <groupId>mysql</groupId>
    <artifactId>mysql-connector-java</artifactId>
    <version>8.0.26</version>
</dependency>
```
```gradle
dependencies {
    implementation 'mysql:mysql-connector-java:8.0.26'
}
```
driver 
```properties
spring.datasource.driver-class-name=com.mysql.cj.jdbc.Driver
```
Dialect <br>
For MySQL 5.x:
```properties
spring.jpa.properties.hibernate.dialect: org.hibernate.dialect.MySQL5InnoDBDialect
```
For MySQL 8.x:
```properties
spring.jpa.properties.hibernate.dialect: org.hibernate.dialect.MySQL8Dialect
```
