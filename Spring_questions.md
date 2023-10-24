21) How can you access a value defined in the application? What is properties file in Spring Boot?

Use the @Value annotation to access the properties which is defined in the application – properties file.

```java
@Value("${custom.value}")
private String customVal;
```

38) What is @pathVariable?
@PathVariable annotation helps you to extract information from the URI directly.

