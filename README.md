# jpa-multiple-data-source-oracle-mysql
    JPA多数据源之Oracle——MySQL
    基本配置与双[mysql](https://github.com/g1335333249/jpa-multiple-data-source-mysql-mysql)情况相同
    仅需在第二个mysql数据源中添加Mysql的方言
```java
    @Bean("entityManagerFactorySecondary")
    public LocalContainerEntityManagerFactoryBean entityManagerFactorySecondary(EntityManagerFactoryBuilder builder) {
        Map<String, String> param = new HashMap<>();
        param.put("hibernate.dialect", "org.hibernate.dialect.MySQL5Dialect");
        jpaProperties.setProperties(param);
        return builder.dataSource(dataSourceSecondary).packages("com.example.oracle.entity.secondary").persistenceUnit("secondaryPersistenceUnit").properties(jpaProperties.getHibernateProperties(new HibernateSettings())).build();
    }
```
