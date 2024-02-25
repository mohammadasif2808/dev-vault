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

#### 0.0.2-Error
```Caused by: java.lang.reflect.InaccessibleObjectException: Unable to make protected final java.lang.Class java.lang.ClassLoader.defineClass(java.lang.String,byte[],int,int,java.security.ProtectionDomain) throws java.lang.ClassFormatError accessible: module java.base does not "opens java.lang" to unnamed module @4b553d26```

#### Resolution

To resolve this issue, you can try the following solutions: <br>
1.Downgrade to Java 8: If you can downgrade your Java version, using Java 8 will likely resolve the issue since JPMS was not introduced until Java 9.
2.Upgrade Spring Boot and Spring: Upgrade to a newer version of Spring Boot (2.1.x or later) and Spring (5.1.x or later) that better supports Java 9+ modules.

