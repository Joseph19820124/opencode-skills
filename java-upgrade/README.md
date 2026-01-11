# Java 21 + Spring Boot 3 Upgrade Skill

A skill for Claude Code that automates the upgrade of Java Maven projects from Java 8/11/17 and Spring Boot 2.x to Java 21 and Spring Boot 3.x.

## Overview

This skill provides comprehensive guidance and automation for upgrading Java projects, including:

- ☕ Java version upgrade to 21
- 🚀 Spring Boot upgrade to 3.x (latest stable)
- 📦 Jakarta EE namespace migration (javax.* → jakarta.*)
- 🔧 Dependency compatibility updates
- 🔒 Spring Security 6 migration
- 💾 Hibernate 6 compatibility

## Installation

### Prerequisites

- [Claude Code](https://github.com/anthropics/claude-code) installed
- Java Maven project

### Install the Skill

```bash
# Clone from the opencode-skills repository
cd ~/.config/opencode/skill
git clone https://github.com/Joseph19820124/opencode-skills.git temp
mv temp/java-upgrade ./
rm -rf temp
```

Or manually download and place the `java-upgrade` folder in `~/.config/opencode/skill/`.

## Usage

In your Claude Code session, navigate to your Java project and run:

```bash
/java-upgrade
```

Claude will automatically:

1. Analyze your current `pom.xml`
2. Update Spring Boot and Java versions
3. Migrate all javax.* imports to jakarta.*
4. Update Spring Security configuration (if applicable)
5. Update deprecated configuration properties
6. Test the compilation and run tests

## What Gets Upgraded

### Version Updates

- **Java**: 8/11/17 → 21
- **Spring Boot**: 2.x → 3.4.1
- **Spring Cloud**: Compatible versions (if used)

### Namespace Migrations

All `javax.*` packages are migrated to `jakarta.*`:

- `javax.persistence.*` → `jakarta.persistence.*`
- `javax.validation.*` → `jakarta.validation.*`
- `javax.servlet.*` → `jakarta.servlet.*`
- `javax.annotation.*` → `jakarta.annotation.*`
- And more...

### Framework Updates

- **Spring Security**: Migrates from `WebSecurityConfigurerAdapter` to `SecurityFilterChain`
- **Spring Data**: Updates repository patterns
- **Hibernate**: Compatibility updates for Hibernate 6

## Example

Before running the skill, your project might look like:

```xml
<parent>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-parent</artifactId>
    <version>2.7.0</version>
</parent>

<properties>
    <java.version>11</java.version>
</properties>
```

After the upgrade:

```xml
<parent>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-parent</artifactId>
    <version>3.4.1</version>
</parent>

<properties>
    <java.version>21</java.version>
</properties>
```

## Verification Steps

The skill ensures your upgrade is successful by:

- ✅ Compiling the project (`mvn clean compile`)
- ✅ Running tests (`mvn test`)
- ✅ Starting the application (`mvn spring-boot:run`)

## Common Issues Handled

- Jakarta EE namespace conflicts
- Spring Security configuration migration
- Deprecated property updates
- Dependency version conflicts
- Hibernate 6 compatibility

## Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

### How to Contribute

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

## Resources

- [Spring Boot 3.0 Migration Guide](https://github.com/spring-projects/spring-boot/wiki/Spring-Boot-3.0-Migration-Guide)
- [Jakarta EE 9 Migration](https://jakarta.ee/specifications/)
- [Spring Security 6.0 Migration](https://docs.spring.io/spring-security/reference/migration/index.html)

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Support

If you encounter any issues or have questions:

- Open an issue in this repository
- Check the [Claude Code documentation](https://github.com/anthropics/claude-code)

## Acknowledgments

Built for use with [Claude Code](https://github.com/anthropics/claude-code) by Anthropic.
