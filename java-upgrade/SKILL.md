---
name: java-upgrade
description: Upgrade Java Maven projects from Java 8/11/17 and Spring Boot 2.x to Java 21 and Spring Boot 3.x
license: MIT
compatibility: opencode
metadata:
  language: java
  framework: spring-boot
---

# Java 21 + Spring Boot 3 Upgrade Skill

This skill helps you upgrade Java Maven projects to Java 21 and Spring Boot 3.x.

## Overview

Perform a comprehensive upgrade of Java projects including:
- Java version upgrade to 21
- Spring Boot upgrade to 3.x (latest stable)
- Jakarta EE namespace migration (javax.* -> jakarta.*)
- Dependency compatibility updates

## Step-by-Step Upgrade Process

### 1. Analyze Current Project

First, read and analyze the project's `pom.xml` to understand:
- Current Java version
- Current Spring Boot version
- All dependencies and their versions
- Any plugins that need updating

### 2. Update pom.xml

Make the following changes to `pom.xml`:

#### 2.1 Update Spring Boot Parent
```xml
<parent>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-parent</artifactId>
    <version>3.4.1</version>
    <relativePath/>
</parent>
```

#### 2.2 Update Java Version
```xml
<properties>
    <java.version>21</java.version>
</properties>
```

#### 2.3 Update Dependencies (if explicitly versioned)
Common dependency updates for Spring Boot 3:
- spring-boot-starter-* -> 3.4.1
- spring-cloud-* -> 2023.0.x (if using Spring Cloud)
- Remove any javax.* dependencies, replace with jakarta.*

### 3. Jakarta EE Namespace Migration

Spring Boot 3 uses Jakarta EE 9+ which requires namespace changes.

#### 3.1 Find and Replace Imports
Search all Java files and replace:
- `javax.persistence.*` -> `jakarta.persistence.*`
- `javax.validation.*` -> `jakarta.validation.*`
- `javax.servlet.*` -> `jakarta.servlet.*`
- `javax.annotation.*` -> `jakarta.annotation.*`
- `javax.transaction.*` -> `jakarta.transaction.*`
- `javax.websocket.*` -> `jakarta.websocket.*`
- `javax.mail.*` -> `jakarta.mail.*`
- `javax.activation.*` -> `jakarta.activation.*`

#### 3.2 Update Dependencies in pom.xml
Replace javax dependencies:
```xml
<!-- Old -->
<dependency>
    <groupId>javax.validation</groupId>
    <artifactId>validation-api</artifactId>
</dependency>

<!-- New -->
<dependency>
    <groupId>jakarta.validation</groupId>
    <artifactId>jakarta.validation-api</artifactId>
</dependency>
```

### 4. Code Changes Required for Spring Boot 3

#### 4.1 Spring Security Changes (if applicable)
- `WebSecurityConfigurerAdapter` is removed - use `SecurityFilterChain` bean instead
- `authorizeRequests()` -> `authorizeHttpRequests()`
- `antMatchers()` -> `requestMatchers()`

Example migration:
```java
// Old (Spring Boot 2.x)
@Configuration
public class SecurityConfig extends WebSecurityConfigurerAdapter {
    @Override
    protected void configure(HttpSecurity http) throws Exception {
        http.authorizeRequests()
            .antMatchers("/public/**").permitAll()
            .anyRequest().authenticated();
    }
}

// New (Spring Boot 3.x)
@Configuration
public class SecurityConfig {
    @Bean
    public SecurityFilterChain securityFilterChain(HttpSecurity http) throws Exception {
        http.authorizeHttpRequests(auth -> auth
            .requestMatchers("/public/**").permitAll()
            .anyRequest().authenticated()
        );
        return http.build();
    }
}
```

#### 4.2 Spring Data Changes (if applicable)
- `CrudRepository.findById()` now returns `Optional<T>`
- Some query method naming conventions have changed

#### 4.3 Hibernate 6 Changes (if using JPA)
- ID generation strategies may need updates
- Some HQL syntax changes

### 5. Configuration Changes

#### 5.1 application.properties / application.yml Updates
Check for deprecated properties:
- `spring.redis.*` -> `spring.data.redis.*`
- `spring.elasticsearch.*` -> `spring.elasticsearch.uris`
- Various other property renames (run the app to see deprecation warnings)

### 6. Test the Upgrade

After making changes:
1. Run `mvn clean compile` to check for compilation errors
2. Run `mvn test` to verify tests pass
3. Run `mvn spring-boot:run` to verify application starts

### 7. Common Issues and Solutions

#### Issue: Compilation errors with javax imports
Solution: Run a global find/replace for javax -> jakarta namespaces

#### Issue: Spring Security not working
Solution: Migrate from WebSecurityConfigurerAdapter to SecurityFilterChain

#### Issue: JPA/Hibernate errors
Solution: Update entity annotations and check ID generation strategies

#### Issue: Missing dependencies
Solution: Check for removed/renamed dependencies in Spring Boot 3

## Checklist

Before completing the upgrade, verify:
- [ ] pom.xml updated with Spring Boot 3.x and Java 21
- [ ] All javax.* imports changed to jakarta.*
- [ ] Spring Security migrated (if applicable)
- [ ] application.properties updated for deprecated properties
- [ ] Project compiles without errors (`mvn clean compile`)
- [ ] Tests pass (`mvn test`)
- [ ] Application starts successfully (`mvn spring-boot:run`)

## References

- [Spring Boot 3.0 Migration Guide](https://github.com/spring-projects/spring-boot/wiki/Spring-Boot-3.0-Migration-Guide)
- [Jakarta EE 9 Migration](https://jakarta.ee/specifications/)
- [Spring Security 6.0 Migration](https://docs.spring.io/spring-security/reference/migration/index.html)
